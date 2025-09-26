<template>
  <main>
    <article v-if="innerHtml" v-html="innerHtml"></article>
    <article v-else>{{ message }}</article>
  </main>
</template>

<script setup>
import { ref, watchEffect } from 'vue'
import { useRoute } from 'vue-router'
import MarkdownIt from 'markdown-it'

const route = useRoute()
const newMd = new MarkdownIt({ html: true })
const innerHtml = ref('')
const message = ref('Loading...')

function stripFrontmatter(source) {
  if (!source) return ''
  return source.replace(/^---[\s\S]*?---\s*/, '')
}

// glob all markdown files in the blogPosts folder as raw text
const mdModules = import.meta.glob('../components/blogPosts/*.md', { as: 'raw' })

async function loadMarkdownFromParam(param) {
  if (!param) return ''
  const rawParam = String(param)
  const filename = rawParam.split('/').pop()
  // matches whether it's "blogPost1.md" or "BlogPost1.md" or "blogpost1"
  const candidates = []
  if (filename.toLowerCase().endsWith('.md')) {
    candidates.push(filename)
    candidates.push(filename.toLowerCase())
    candidates.push(filename.toUpperCase())
  } else {
    candidates.push(
      `${filename}.md`,
      `${filename.toLowerCase()}.md`,
      `${filename.toUpperCase()}.md`,
    )
  }

  const matchKey = Object.keys(mdModules).find((key) => {
    const base = key.split('/').pop()
    return candidates.some((c) => base === c || base.toLowerCase() === c.toLowerCase())
  })

  if (!matchKey) {
    throw new Error(`Markdown file not found for "${filename}"`)
  }

  // load the raw string
  const loader = mdModules[matchKey]
  const raw = await loader()
  return stripFrontmatter(raw)
}

watchEffect(async () => {
  try {
    const link = route.params.link
    if (!link) {
      message.value = 'No post specified'
      innerHtml.value = ''
      return
    }
    message.value = 'Loading...'
    const markdown = await loadMarkdownFromParam(link)
    innerHtml.value = newMd.render(markdown)
    message.value = ''
  } catch (err) {
    console.error(err)
    message.value = `Error: ${err.message}`
    innerHtml.value = ''
  }
})
</script>

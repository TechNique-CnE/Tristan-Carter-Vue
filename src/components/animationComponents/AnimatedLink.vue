<script setup>
import { inject, computed, useSlots } from 'vue'
import { RouterLink } from 'vue-router'

defineProps({
  to: {
    type: String,
    required: true,
  },
})

const animationClass = inject('animationClass')
const slots = useSlots()

function extractText(vnodes) {
  if (!vnodes) return ''
  return vnodes
    .map((v) => {
      if (typeof v.children === 'string') return v.children
      if (Array.isArray(v.children)) return extractText(v.children)
      return ''
    })
    .join('')
}

const slotContent = computed(() => extractText(slots.default ? slots.default() : []))

// CSS content needs a quoted string for content: var(--dynamic-content)
// produce a properly escaped quoted value for the CSS variable
const cssVarContent = computed(() => {
  const txt = slotContent.value || ''
  return `'${String(txt).replace(/'/g, "\\'")}'`
})
</script>

<template>
  <RouterLink
    :to="to"
    class="animated-link"
    :class="animationClass"
    :aria-label="slotContent"
    :style="{ '--dynamic-content': cssVarContent }"
  >
    <slot />
  </RouterLink>
</template>

<style scoped>
/* add imports for all link animations when created
   styles are based on the injected animationClass
*/
@import '../../styles/glitch.css';
</style>

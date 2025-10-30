<script setup>
import { ref, inject, onMounted, onBeforeUnmount } from 'vue'
const isOpen = ref(true)

const themeBtn = ref(null)
const btnBtm = ref(null)
const btnWidth = ref(null)
const btnLeft = ref(null)
const btnMid = ref(null)
const topValue = ref('55px')
const leftValue = ref('60%')

function updateValues() {
  console.log(themeBtn.value.getBoundingClientRect())
  btnBtm.value = themeBtn.value.getBoundingClientRect().bottom
  btnLeft.value = themeBtn.value.getBoundingClientRect().left
  btnWidth.value = themeBtn.value.getBoundingClientRect().width / 2
  btnMid.value = btnLeft.value + btnWidth.value

  leftValue.value = btnMid.value + 'px'
  topValue.value = btnBtm.value + 'px'
}

onMounted(() => {
  updateValues()
  window.addEventListener('resize', () => {
    updateValues()
  })
})

onBeforeUnmount(() => {
  window.removeEventListener('resize')
})

const { updateClass } = inject('animationClass')
</script>

<!-- SVGs from SVG repo.com -->

<template>
  <div class="theme-container">
    <button @click="isOpen = !isOpen" class="nav-link" :class="{ active: isOpen }" ref="themeBtn">
      Themes
    </button>

    <teleport to="body">
      <div
        class="theme-box"
        v-show="isOpen"
        :class="{ active: isOpen }"
        :style="{ top: topValue, left: leftValue }"
      >
        <div>
          <button @click="updateClass(null)">
            <svg width="100%" height="100%" viewBox="0 0 24 24" fill="none">
              <path
                id="Vector"
                d="M5.75 5.75L18.25 18.25M12 21C7.02944 21 3 16.9706 3 12C3 7.02944 7.02944 3 12 3C16.9706 3 21 7.02944 21 12C21 16.9706 16.9706 21 12 21Z"
                stroke="#000000"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              ></path>
            </svg>
          </button>
          None
        </div>
        <div>
          <button @click="updateClass('glitch')">
            <svg
              width="100%"
              height="100%"
              viewBox="-1.8 -1.8 19.6 19.6"
              fill="none"
              stroke="#08f508"
              stroke-width="1"
            >
              <path
                d="M7 0V1.60002C7.32311 1.53443 7.65753 1.5 8 1.5C8.34247 1.5 8.67689 1.53443 9 1.60002V0H11V2.49963C11.8265 3.12041 12.4543 3.99134 12.7711 5H3.2289C3.5457 3.99134 4.17354 3.12041 5 2.49963V0H7Z"
                fill="#000000"
              ></path>
              <path
                d="M0 7V9H3V10.4957L0.225279 11.2885L0.774721 13.2115L3.23189 12.5095C3.87194 14.5331 5.76467 16 8 16C10.2353 16 12.1281 14.5331 12.7681 12.5095L15.2253 13.2115L15.7747 11.2885L13 10.4957V9H16V7H9V12H7V7H0Z"
                fill="#000000"
              ></path>
            </svg>
          </button>
          Glitch
        </div>
        <div>
          <button @click="updateClass(null)"></button>
          Theme 3
        </div>
        <div>
          <button @click="updateClass(null)"></button>
          Theme 4
        </div>
      </div>
    </teleport>
  </div>
</template>

<style scoped>
.theme-container {
  position: relative;
}
button.nav-link {
  font-size: var(--fs-sm);
  list-style: none;
  color: var(--txt-color);
  text-decoration: none;
  padding: 10px 10px 0;
  cursor: pointer;
  background-color: transparent;
  border: 2px solid transparent;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  transition: var(--transition);
  margin-bottom: 10px;
}
button.nav-link:hover {
  border-bottom: 2px solid var(--primary);
  color: var(--primary);
  scale: 1.05;
}
button.nav-link.active {
  color: var(--primary);
  scale: 1.05;
  border-top: var(--border);
  border-right: var(--border);
  border-left: var(--border);
  border-bottom: 2px solid transparent;
}

.theme-box {
  position: absolute;
  transform: translateX(-53.5%);
  display: grid;
  background-color: var(--bg2);
  backdrop-filter: blur(10px);
  grid-template-columns: repeat(3, 1fr);
  width: min(250px, 90%);
  padding: var(--sm-gap);
  gap: var(--sm-gap);
  border-radius: 5px;
}
.theme-box.active {
  border: 2px solid;
  border-image: conic-gradient(at 33% 100%, transparent 0 6%, var(--primary) 6% 100%) 1;
}

.theme-box div {
  font-size: 14px;
  align-items: center;
  display: flex;
  flex-direction: column;
}
.theme-box div button {
  background-color: var(--bg);
  width: 100%;
  aspect-ratio: 1/1;
  border: none;
  cursor: pointer;
  border-radius: 5px;
}
</style>

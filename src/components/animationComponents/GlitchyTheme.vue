<script setup>
import { ref, onMounted } from 'vue'

const maxLines = 10
const maxBoxes = 6
const lineVariations = 5
const boxVariations = 6
const currentLefts = ref([])
const linesList = ref([])

function getRandom(limit) {
  return Math.floor(Math.random() * limit)
}

function getRandomLeft() {
  let left = getRandom(20) * 5
  let leftInArr = currentLefts.value.indexOf(left) !== -1
  while (leftInArr) {
    left += 5
    left %= 100
    leftInArr = currentLefts.value.indexOf(left) !== -1
  }
  currentLefts.value.push(left)
  return left
}

function getUniqueBoxes(limit) {
  const available = Array.from({ length: boxVariations }, (_, i) => i + 1)
  const take = Math.min(limit, available.length)
  for (let i = available.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1))
    ;[available[i], available[j]] = [available[j], available[i]]
  }
  return available.slice(0, take)
}

function createLine() {
  const left = getRandomLeft()
  return {
    id: left,
    left,
    animationDelay: getRandom(8),
    lineVariation: getRandom(lineVariations) + 1,
    boxes: getUniqueBoxes(maxBoxes),
  }
}

function addLineToList() {
  const line = createLine()
  linesList.value.push(line)
  return line
}

onMounted(() => {
  while (linesList.value.length < maxLines) {
    addLineToList()
  }
})
</script>

<template>
  <div
    v-for="line in linesList"
    :key="line.id"
    class="matrix-line"
    :class="'matrix-line' + line.lineVariation"
    :style="{ left: line.left + '%', animationDelay: line.animationDelay + 's' }"
  >
    <div
      v-for="(box, boxIndex) in line.boxes"
      :key="boxIndex"
      class="matrix-box"
      :class="'matrix-box' + box"
    ></div>
  </div>
</template>

<style scoped>
@keyframes fallingLine {
  0% {
    transform: translateY(-100%);
  }
  100% {
    transform: translateY(100vh);
  }
}
@keyframes changeLetter1 {
  0%,
  100% {
    content: 'X';
  }
  20% {
    content: 'D';
  }
  40% {
    content: '5';
  }
  60% {
    content: '/';
  }
  80% {
    content: 'P';
  }
}
@keyframes changeLetter2 {
  0%,
  100% {
    content: '@';
  }
  20% {
    content: '7';
  }
  40% {
    content: 'W';
  }
  60% {
    content: '2';
  }
  80% {
    content: 'C';
  }
}
@keyframes changeLetter3 {
  0%,
  100% {
    content: 'H';
  }
  20% {
    content: 'A';
  }
  40% {
    content: '?';
  }
  60% {
    content: 'R';
  }
  80% {
    content: '(';
  }
}
@keyframes changeLetter4 {
  0%,
  100% {
    content: 'S';
  }
  20% {
    content: '#';
  }
  40% {
    content: 'I';
  }
  60% {
    content: '&';
  }
  80% {
    content: 'Z';
  }
}
@keyframes changeLetter5 {
  0%,
  100% {
    content: 'Q';
  }
  20% {
    content: 'T';
  }
  40% {
    content: '9';
  }
  60% {
    content: 'Y';
  }
  80% {
    content: 'F';
  }
}
@keyframes changeLetter6 {
  0%,
  100% {
    content: 'U';
  }
  20% {
    content: '%';
  }
  40% {
    content: '4';
  }
  60% {
    content: 'O';
  }
  80% {
    content: 'E';
  }
}
.matrix-line {
  position: absolute;
  display: flex;
  flex-direction: column-reverse;
  text-align: left;
  transform: translateY(-100%);
}
.matrix-line1 {
  animation: fallingLine 10s linear infinite;
  font-size: 24px;
}
.matrix-line2 {
  animation: fallingLine 12s linear infinite;
  font-size: 20px;
}
.matrix-line3 {
  animation: fallingLine 14s linear infinite;
  font-size: 26px;
}
.matrix-line4 {
  animation: fallingLine 16s linear infinite;
  font-size: 12px;
}
.matrix-line5 {
  animation: fallingLine 18s linear infinite;
  font-size: 8px;
}
.matrix-box {
  color: var(--primary);
  display: block;
  text-shadow: 0 0 16px var(--primary);
}
.matrix-box:nth-child(2) {
  opacity: 0.75;
}
.matrix-box:nth-child(3) {
  opacity: 0.6;
}
.matrix-box:nth-child(4) {
  opacity: 0.45;
}
.matrix-box:nth-child(5) {
  opacity: 0.3;
}
.matrix-box:nth-child(6) {
  opacity: 0.15;
}
.matrix-box::after {
  content: 'X';
  font-family: monospace;
}
.matrix-box1::after {
  animation: changeLetter1 3s linear infinite;
}
.matrix-box2::after {
  animation: changeLetter2 3s linear infinite;
}
.matrix-box3::after {
  animation: changeLetter3 3s linear infinite;
}
.matrix-box4::after {
  animation: changeLetter4 3s linear infinite;
}
.matrix-box5::after {
  animation: changeLetter5 3s linear infinite;
}
.matrix-box6::after {
  animation: changeLetter6 3s linear infinite;
}
</style>

<template>
  <NavBar background="dark" text="white" :sticky="true" :overlay="false" />

  <section class="hero">
    <div class="hero-content">
      <h1 class="headline">Unsere Galerie</h1>
      <p class="subline"></p>
    </div>
  </section>

  <h2 class="überschrift">Ordination Bad Ischl</h2>
  <section class="grid">
    <div class="box" v-for="(img, index) in BadIschlImages" :key="index">
      <img :src="img" width="500px" @click="openBigImgMaria(index)" />
    </div>
  </section>

  <div class="BigImgOverlay" v-if="showBigImg">
    <button class="btnLeft" @click="left()">←</button>
    <img class="bigImg" :src="currentImg" />
    <button class="btnRight" @click="right()">→</button>
    <button class="btnClose" @click="closeBigImg()">×</button>
  </div>
  <Footer />
</template>

<script setup lang="ts">
import { ref } from 'vue'
import NavBar from '@/components/NavBar.vue'
import Footer from '@/components/FooterComponent.vue'
import { parseImagePath } from '@/helpers'

const BadIschlImages = [
  parseImagePath('img/Ordi_4820/Ordi00_7537_pp.jpg'),
  parseImagePath('img/Ordi_4820/Ordi01_7591.jpg'),
  parseImagePath('img/Ordi_4820/Ordi02_7595.jpg'),
  parseImagePath('img/Ordi_4820/Ordi03_7602.jpg'),
  parseImagePath('img/Ordi_4820/Ordi04_7608.jpg'),
  parseImagePath('img/Ordi_4820/Ordi05_7615.jpg'),
  parseImagePath('img/Ordi_4820/Ordi06_7692.jpg'),
  parseImagePath('img/Ordi_4820/Ordi07_7628.jpg'),
  parseImagePath('img/Ordi_4820/Ordi08_7680.jpg'),
  parseImagePath('img/Ordi_4820/Ordi09_7657.jpg'),
  parseImagePath('img/Ordi_4820/Ordi10_7632.jpg'),
  parseImagePath('img/Ordi_4820/Ordi11_7645.jpg'),
  parseImagePath('img/Ordi_4820/Ordi12_7660.jpg'),
  parseImagePath('img/Ordi_4820/Ordi13_7682.jpg'),
  parseImagePath('img/Ordi_4820/Ordi14_7684.jpg'),
  parseImagePath('img/Ordi_4820/Ordi15_7694.jpg'),
  parseImagePath('img/Ordi_4820/Ordi16_7662.jpg'),
  parseImagePath('img/Ordi_4820/Ordi17_7663.jpg'),
  parseImagePath('img/Ordi_4820/Ordi18_7671.jpg'),
  parseImagePath('img/Ordi_4820/Ordi19_7672.jpg'),
  parseImagePath('img/Ordi_4820/Ordi20_7665.jpg'),
  parseImagePath('img/Ordi_4820/Ordi21_7669.jpg'),
  parseImagePath('img/Ordi_4820/Ordi22_7673.jpg'),
  parseImagePath('img/Ordi_4820/Ordi23_7687.jpg'),
  parseImagePath('img/Ordi_4820/Ordi24_7702.jpg'),
]

const showBigImg = ref(false)
const currentImg = ref('')

function openBigImgMaria(index: number) {
  currentImg.value = BadIschlImages[index]
  showBigImg.value = true
}

function closeBigImg() {
  showBigImg.value = false
}

function right() {
  if (currentImg.value.includes('1070')) {
    const index = BadIschlImages.indexOf(currentImg.value)
    const nextIndex = (index + 1) % BadIschlImages.length
    openBigImgMaria(nextIndex)
  }
}

function left() {
  if (currentImg.value.includes('1070')) {
    const index = BadIschlImages.indexOf(currentImg.value)
    const nextIndex = (index - 1) % BadIschlImages.length
    openBigImgMaria(nextIndex)
  }
}
</script>

<style scoped lang="scss">
.hero {
  width: 100%;
  padding: 140px 20px 100px;
  background: linear-gradient(135deg, $primary, $secondary);
  color: white;
  text-align: center;
  clip-path: polygon(0 0, 100% 0, 100% 85%, 0 100%);
}

.hero-content {
  max-width: 1300px;
  margin: 0 auto;
}

.headline {
  font-size: 2.4rem;
  font-weight: 700;
  margin-bottom: 10px;
}

.überschrift {
  font-size: 3rem;
  margin: 2rem 0 1rem 0;
  color: $primary;
  font-weight: 500;
  text-align: center;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 30px;
  padding: 30px;
}

.box {
  display: flex;
  justify-content: center;
}

.box img {
  width: 100%;
  max-width: 500px;
  height: 400px;
  object-fit: cover;
  border-radius: 25px;
  border: 3px solid $primary;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  cursor: pointer;
}

.box img:hover {
  transform: scale(1.03);
  box-shadow: 0 10px 25px $primary;
}

.BigImgOverlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.9);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.BigImgOverlay .bigImg {
  max-width: 90%;
  max-height: 90%;
  object-fit: contain;
  border-radius: 10px;
}

.BigImgOverlay button {
  position: absolute;
  background-color: $primary;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;
  font-size: 2rem;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: all 0.3s ease;
}

.BigImgOverlay .btnClose {
  top: 20px;
  right: 20px;
}

.BigImgOverlay .btnLeft {
  left: 20px;
  top: 50%;
  transform: translateY(-50%);
}

.BigImgOverlay .btnRight {
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
}

.BigImgOverlay .btnClose:hover,
.BigImgOverlay .btnLeft:hover,
.BigImgOverlay .btnRight:hover {
  background-color: $secondary;
  border-radius: 30%;
  width: 55px;
  height: 55px;
}
</style>

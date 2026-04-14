<template>
  <div v-show="isVisible" @click="hideScreen()" class="splashscreen">
    <div
      class="text-center full-width full-height"
      :style="{
        backgroundImage: 'url(' + backgroundImagePath + ')',
      }"
    >
      <div class="fixed-center text-secondary">
        <q-img src="@/assets/icons/Logo.svg" width="15rem" class="animationTarget hide" />

        <span class="text-h3 q-mt-sm text-bold block hide animationTarget"
          >Zahnmedizin, die zu Ihnen passt!</span
        >
        <span class="text-h4 q-mt-md border-seperator font-TradeGothic block hide animationTarget"
          >Zeit für klare Beratungsgespräche und gemeinsame Entscheidungen</span
        >
        <span class="text-h5 text-italic q-mt-lg block hide animationTarget">Dr. med. dent.</span>
        <span class="text-h1 block q-mb-xl hide animationTarget">Isabelle Olivia</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Ref } from 'vue'
import { onMounted, onUnmounted, ref } from 'vue'
import { parseImagePath } from '@/helpers'

let isVisible: Ref<boolean> = ref(true)
let backgroundImagePath = parseImagePath('img/splashscreen_bg.jpg')
let animationTimeouts: number[] = []
let hideTimeout: number[] = []
let animationTargets: NodeListOf<Element>

// disable scroll
document.body.style.overflow = 'hidden'

onMounted(() => {
  animationTargets = document.querySelectorAll('.animationTarget')

  animationTargets.forEach((item, i) => {
    animationTimeouts.push(
      setTimeout(() => {
        item.classList.replace('hide', 'show')
      }, i * 750),
    )
  })

  hideTimeout.push(
    setTimeout(() => {
      hideScreen()
    }, 6000),
  ) // 6 seconds
})

onUnmounted(() => {
  hideTimeout.forEach((timeout) => {
    clearTimeout(timeout)
  })
})

function hideScreen() {
  document.querySelector('.splashscreen')?.classList.add('hide-splashscreen')

  hideTimeout.push(
    setTimeout(() => {
      isVisible.value = false
      document.body.style.overflow = 'visible'
    }, 750),
  )

  animationTimeouts.forEach((timeout) => {
    clearTimeout(timeout)
  })
}
</script>

<style scoped lang="scss">
.splashscreen {
  position: absolute;
  top: 0px;

  width: 100vw;
  height: 100vh;
  z-index: 10;

  background-color: white;
}

@keyframes ease-opacity {
  from {
    opacity: 0%;
  }

  to {
    opacity: 100%;
  }
}

.hide {
  opacity: 0%;
}

.show {
  animation: ease-opacity 0.75s ease-in 0s 1 normal forwards;
}

.hide-splashscreen {
  animation: ease-opacity 0.75s ease-in 0s 1 reverse forwards;
}

.border-seperator {
  border-bottom: 5px solid $primary;
}
</style>

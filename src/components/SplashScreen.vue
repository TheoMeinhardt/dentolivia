<template>
  <div v-show="isVisible" @click="hideScreen()" class="splashscreen">
    <div
      class="text-center full-width full-height"
      :style="{
        backgroundImage: 'url(' + backgroundImagePath + ')',
      }"
    >
      <div class="fixed-center text-secondary">
        <q-img src="@/assets/icons/Logo.svg" width="20vh" class="animationTarget hide" />

        <span class="gt-sm text-h3 q-mt-sm text-bold block hide animationTarget"
          >Zahnmedizin, die zu Ihnen passt!</span
        >
        <span class="lt-md text-h5 q-mt-sm text-bold block hide animationTarget"
          >Zahnmedizin, die zu Ihnen passt!</span
        >

        <span
          class="gt-sm text-h4 q-mt-md border-seperator font-TradeGothic block hide animationTarget"
          >Zeit für klare Beratungsgespräche und gemeinsame Entscheidungen</span
        >
        <span
          class="lt-md text-h6 q-mt-md border-seperator font-TradeGothic block hide animationTarget"
          >Zeit für klare Beratungsgespräche und gemeinsame Entscheidungen</span
        >

        <span class="gt-sm text-h5 text-italic q-mt-lg block hide animationTarget"
          >Dr. med. dent.</span
        >
        <span class="lt-md text-h6 text-italic q-mt-lg block hide animationTarget"
          >Dr. med. dent.</span
        >
        <span class="gt-sm text-h1 block q-mb-xl hide animationTarget">Isabelle Olivia</span>
        <span class="lt-md text-h3 block q-mb-xl hide animationTarget">Isabelle Olivia</span>

        <div class="text-right hide animationTarget">
          <q-icon :name="animatedIconName" size="2rem" style="transform: rotate(-35deg)"></q-icon>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Ref } from 'vue'
import { computed, onMounted, onUnmounted, ref } from 'vue'
import { parseImagePath } from '@/helpers'

const isVisible: Ref<boolean> = ref(true)
const backgroundImagePath = parseImagePath('img/splashscreen_bg.jpg')
const hideTimeout: number[] = []
let animationTimeouts: number[] = []
let animationIntervals: number[] = []
let animationTargets: NodeListOf<Element>
let clickIconName = ref('fa-solid fa-hand-pointer')

onMounted(() => {
  // disable scroll
  document.body.style.overflow = 'hidden'

  animationTargets = document.querySelectorAll('.animationTarget')

  animationTargets.forEach((item, i) => {
    animationTimeouts.push(
      setTimeout(() => {
        item.classList.replace('hide', 'show')
      }, i * 750),
    )
  })

  animationIntervals.push(
    setInterval(() => {
      if (clickIconName.value === 'fa-solid fa-hand-pointer') {
        clickIconName.value = 'fa-regular fa-hand-pointer'
      } else {
        clickIconName.value = 'fa-solid fa-hand-pointer'
      }
    }, 750),
  )

  hideTimeout.push(
    setTimeout(() => {
      hideScreen()
    }, 10000),
  ) // 10 seconds
})

const animatedIconName = computed(() => {
  return clickIconName.value
})

onUnmounted(() => {
  document.body.style.overflow = 'visible'
  hideTimeout.forEach((timeout) => {
    clearTimeout(timeout)
  })

  animationIntervals.forEach((interval) => {
    clearInterval(interval)
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

  animationIntervals.forEach((interval) => {
    clearInterval(interval)
  })
}
</script>

<style scoped lang="scss">
.splashscreen {
  position: fixed;
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

<template>
  <div v-show="isVisible" @click="hideScreen()" class="splashscreen">
    <div class="text-center full-width full-height" :style="{
      'backgroundImage':
        'url(' + backgroundImagePath + ')'
    }">

      <div class="fixed-center text-secondary">

        <q-img id="animationTarget" src="@/assets/icons/Logo.svg" width="15rem" class="hide" />

        <span id="animationTarget" class="text-h3 q-mt-sm text-bold block hide ">Zahnmedizin, die zu Ihnen
          passt!</span>
        <span id="animationTarget" class="text-h4 q-mt-md border-seperator font-TradeGothic block hide">Zeit für klare
          Beratungsgespräche
          und gemeinsame Entscheidungen</span>
        <span id="animationTarget" class="text-h5 text-italic q-mt-lg block hide">Dr. med. dent.</span>
        <span id="animationTarget" class="text-h1 block q-mb-xl hide">Isabelle Olivia</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Ref } from "vue"
import { onMounted, ref } from "vue"
import { parseImagePath } from "@/helpers"

let isVisible: Ref<boolean> = ref(true)
let backgroundImagePath = parseImagePath("img/splashscreen_bg.jpg")
let animationTargets

// disable scroll
document.body.style.overflow = "hidden"

onMounted(() => {
  animationTargets = document.querySelectorAll("#animationTarget")

  animationTargets.forEach((item, i) => {
    setTimeout(() => {
      item.classList.replace("hide", "show")
    }, i * 750)
  })
})

function hideScreen() {
  document.querySelector(".splashscreen")?.classList.add("hide-splashscreen")
  console.log(document.querySelector(".splashscreen"))

  setTimeout(() => {
    isVisible.value = false
    document.body.style.overflow = "visible"
  }, 750)
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
  animation: ease-opacity .75s ease-in 0s 1 normal forwards;
}

.hide-splashscreen {
  animation: ease-opacity .75s ease-in 0s 1 reverse forwards;
}

.border-seperator {
  border-bottom: 5px solid $primary;
}
</style>

<template>
  <div v-show="isVisible" @click="hideScreen()" class="splashscreen">
    <h1>Hallo</h1>
  </div>
</template>

<script setup lang="ts">
import type { Ref } from "vue"
import { ref } from "vue"

let isVisible: Ref<boolean> = ref(true)

// disable scroll
document.body.style.overflow = "hidden"

function hideScreen() {
  isVisible.value = false
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
</style>

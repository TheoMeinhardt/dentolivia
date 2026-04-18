<script setup lang="ts">
import { RouterView } from 'vue-router'

import CookieBanner from './components/CookieBanner.vue'
import Splashscreen from './components/SplashScreen.vue'
</script>

<template>
  <CookieBanner />
  <Splashscreen />

  <RouterView />
</template>

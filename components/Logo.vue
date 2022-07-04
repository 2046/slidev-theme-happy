<style>
  .logo img {
    width: 100%;
    height: 100%;
  }
</style>

<template>
  <Transform :scale="props.scale ? scale : 1" :origin="props.origin">
    <img :src="url" />
  </Transform>
</template>

<script setup lang="ts">
  import { inject } from 'vue'
  import { injectionSlideScale } from '@slidev/client/constants'

  const props = defineProps<{
    url: string
    scale?: boolean
    origin?: string
  }>()

  const scale = inject(injectionSlideScale)
</script>

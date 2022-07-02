<style>
  .logo img {
    width: 100%;
    height: 100%;
  }
</style>
<template>
  <Transform :scale="props.scale ? scale : 1" :origin="props.origin">
    <div class="logo" :style="style">
      <img :src="url" />
    </div>
  </Transform>
</template>
<script setup lang="ts">
  import { computed, inject } from 'vue'
  import { injectionSlideScale } from '@slidev/client/constants'

  const props = defineProps<{
    url: string
    width: number
    height: number
    scale?: boolean
    origin?: string
  }>()

  const style = computed(() => {
    return {
      width: props.width,
      height: props.height
    }
  })

  const scale = inject(injectionSlideScale)
</script>

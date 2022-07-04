<style scoped>
  .full {
    padding: 0;
  }
</style>

<template>
  <div class="slidev-layout full w-full h-full">
    <slot class="w-full h-full" />
  </div>
</template>

<script setup lang="ts">
  import { onMounted, watch } from 'vue'
  import { currentLayout } from '@slidev/client/logic/nav'

  onMounted(() => {
    updateSlideContentOverflow(isLayout(currentLayout.value, 'full') ? 'visible': '')
  })

  watch(currentLayout, (val) => {
    updateSlideContentOverflow(isLayout(val, 'full') ? 'visible' : '')
  })

  function updateSlideContentOverflow(overflow: string) {
    const element = <HTMLDivElement>document.querySelector('#slide-content')

    if (element) {
      element.style.overflow = overflow
    }
  }

  function isLayout(currentLayout = '', conditionLayout = '') {
    return currentLayout === conditionLayout
  }
</script>

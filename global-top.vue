<style scoped>
    .logo {
      position: absolute;
      top: 8px;
      right: 8px;
    }
</style>

<template>
  <Teleport to="#app" v-if="!showEditor && !isPresenter && logo && logo.url">
    <Logo class="logo" :style="style" :url="logo.url" scale origin="top right" />
  </Teleport>
</template>

<script setup lang="ts">
  import { computed } from 'vue'
  import { configs } from '@slidev/client/env'
  import { SlidevConfig } from  '@slidev/types'
  import { showEditor } from '@slidev/client/state'
  import { isPresenter } from '@slidev/client/logic/nav'

  interface ISlidevConfig extends SlidevConfig {
    logo?: {
      url: string
      width: number
      height: number
    }
  }

  const { logo } = configs as ISlidevConfig

  const style = computed(() => {
    return logo ? {
      width: logo.width ? `${logo.width}px` : '',
      height: logo.height ? `${logo.height}px` : '',
    } : {}
  })
</script>

<style scoped>
    .logo {
      position: absolute;
      top: 8px;
      right: 8px;
    }
</style>

<template>
  <Teleport to="#app" v-if="!showEditor && !isPresenter && logo">
    <Logo class="logo" :class="klass" :url="logo" scale origin="top right" />
  </Teleport>
</template>

<script setup lang="ts">
  import { computed } from 'vue'
  import { configs } from '@slidev/client/env'
  import { showEditor } from '@slidev/client/state'
  import { isPresenter } from '@slidev/client/logic/nav'

  const logo = <string>configs.themeConfig.logo || ''

  const klass = computed(() => {
    const qs = logo.includes('?') ? logo.substring(logo.indexOf('?') + 1) : ''
    
    return qs ? qs.split(',') : []
  })
</script>

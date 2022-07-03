<template>
  <div ref="element" :style="style">
    <slot />
  </div>
</template>

<script setup lang="ts">
  import { useRoute } from 'vue-router'
  import { ref, onMounted, inject, computed } from 'vue'
  import { injectionSlideScale } from '@slidev/client/constants'
  import { getCurrentInstance, ComponentInternalInstance } from 'vue'

  const props = withDefaults(defineProps<{
    scale?: number
  }>(), {
    scale: 1
  })

  let elementWidth = ref(0)
  let elementHeight = ref(0)

  const route = useRoute()
  const scale = inject(injectionSlideScale)!
  const element = ref<HTMLDivElement | null>(null)
  const hasWithInVSCode = route.query.embedded === "true"
  const hasWithInSlidesOverviewComponentBool = hasWithInSlidesOverviewComponent(getCurrentInstance())

  const style = computed(() => {
    const scaleWidth = elementWidth.value * scale.value
    const scaleHeight = elementHeight.value * scale.value

    return hasWithInSlidesOverviewComponentBool || hasWithInVSCode ? {} : {
      width: elementWidth.value ? `${scaleWidth}px` : '',
      height: elementHeight.value ? `${scaleHeight}px` : '',
      transform: `translate(-${(scaleWidth - elementWidth.value) / 2}px, -${(scaleHeight - elementHeight.value) / 2}px) scale(${props.scale/scale.value})`
    }
  })

  onMounted(() => {
    const { width, height } = getElementSize(element.value)

    if (!isNaN(width)) {
      elementWidth.value = width
    }

    if (!isNaN(height)) {
      elementHeight.value = height
    }
  })

  function getElementSize(element: HTMLElement | null) {
    const { width = '0', height = '0' } = element ? getComputedStyle(element) : {}

    return {
      width: toNumber(width),
      height: toNumber(height)
    }
  }

  function toNumber(number: string) {
    return parseInt(number.replace('px', ''), 10)
  }

  function hasWithInSlidesOverviewComponent(instance: ComponentInternalInstance | null) {
    const parentInstance: any = instance!.parent

    if (parentInstance && parentInstance.type && parentInstance.setupState) {
      if (parentInstance.setupState.gap, parentInstance.setupState.padding && parentInstance.setupState.cardWidth) {
        return parentInstance
      }

      return !hasWithInSlidesOverviewComponent(parentInstance)
    }
  }
</script>

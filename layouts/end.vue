<template>
  <div class="slidev-layout end">
    <div class="text-8xl tracking-wider h-full text-center grid place-content-center select-none">Thanks</div>
  </div>
</template>

<script setup lang="ts">
  import JSConfetti from 'js-confetti'
  import { onMounted, watch } from 'vue'
  import { showEditor } from '@slidev/client/state'
  import { total, currentPage, isPresenter } from '@slidev/client/logic/nav'

  const confetti = new JSConfetti()

  function showConfetti(delay = 0) {
    setTimeout(() => {
      confetti.addConfetti({
        emojis: ['🌈', '⚡️', '💥', '🥳', '🎉', '✨']
      })
    }, delay);
  }

  function showConfettiAnimation() {
    if (isPresenter.value || showEditor.value) {
      return
    }

    if (currentPage.value - total.value === 1) {
      showConfetti()
      showConfetti(400)
    }
  }

  onMounted(() => showConfettiAnimation())
  watch(currentPage, () => showConfettiAnimation())
</script>

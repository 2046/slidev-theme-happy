<template>
  <div class="z-1000">
    <slot />
    <iconoir-chat-bubble-translate class="absolute -top-4 -right-5 opacity-20" @click="speak" />
  </div>
</template>

<script setup lang="ts">
  const props = defineProps<{
    text: string
  }>()

  function speak() {
    if ('speechSynthesis' in window) {
      const msg = new SpeechSynthesisUtterance()
      msg.text = props.text
      window.speechSynthesis.speak(msg)
    } else {
      alert("Sorry, your browser doesn't support text to speech!")
    }
  }
</script>

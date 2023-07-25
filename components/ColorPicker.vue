<script setup lang="ts">
import { computed, ref, watch } from 'vue'
import { useClipboard, useEyeDropper } from '@vueuse/core'

const source = ref('')
const { text, copy, copied, isSupported: isSupportedUseClipboard } = useClipboard({ source })
const { isSupported: isSupportedUseEyeDropper, open, sRGBHex } = useEyeDropper()

const canPlay = computed(() => isSupportedUseClipboard && isSupportedUseEyeDropper)

watch(sRGBHex, () => copy(sRGBHex.value))
</script>

<template>
  <dialog class="border-2 border-black rounded-lg py-8 px-10 mt-6" :open="!canPlay.value">
    お使いの環境ではこのカラーピッカーを使えません
  </dialog>
  <div class="p-8">
    <img
      class="w-full h-auto rounded-lg"
      src="/color_picker/earth.jpg"
      alt="地球の画像"
    />
  </div>
  <button class="absolute top-4 right-4 bg-lime-600 py-3 px-5 rounded text-white" @click="open()">
    👉 EyeDropper Open
  </button>
  <div
    v-if="copied && sRGBHex"
    class="absolute text-center w-48 m-auto bottom-4 left-0 right-0 py-3 px-5 rounded text-white"
    :style="{ backgroundColor: text }"
  >
    Copied {{ text }}
  </div>
</template>

<script setup lang="ts">
import { pausableWatch, useBluetooth } from '@vueuse/core'
import { ref } from 'vue';

// 心拍数
const heartRateValue = ref<undefined | number>(0)

// 心拍数を得たかどうか
const isGettingHeartRate = ref(false)

// 心拍数を表示するかどうか
const shownHeartRate = ref(false)

const {
  isConnected,
  requestDevice,
  device,
  server,
} = useBluetooth({
  acceptAllDevices: true,
  optionalServices: [
    'heart_rate'
  ],
})

/**
 * Bluetoothを通じて心拍数を得る
 */
const getHeartRate = async () => {
  isGettingHeartRate.value = true

  if (!server.value) return

  const heartRateService = await server.value.getPrimaryService('heart_rate')

  const heartRateCharacteristic = await heartRateService.getCharacteristic(
    'heart_rate_measurement',
  )

  heartRateCharacteristic.startNotifications();

  // @ts-ignore
  heartRateCharacteristic.addEventListener('characteristicvaluechanged', (event) => {
    // @ts-ignore
    const value = event.target.value
    if (value.getUint8(0) & 0x01) {
      heartRateValue.value = value.getUint16(1, /*littleEndian=*/true)
    } else {
      heartRateValue.value = value.getUint8(1)
    }
    
  })
}

const { stop } = pausableWatch(isConnected, (newIsConnected) => {
  if (!newIsConnected || !server.value || isGettingHeartRate.value) return
  getHeartRate()
  stop()
})

const handleShownHeartRate = () => {
  shownHeartRate.value = !shownHeartRate.value
}
</script>

<template>
  <div class="relative">
    <button v-if="isConnected" @click="handleShownHeartRate" class="text-blue-700 absolute top-0 -right-1 z-10">●</button>
    <img class="w-17" :class="{ 'heart': isConnected && shownHeartRate }" src="/heart_rate/heart_shape.svg" alt="" />
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
        <span v-if="isConnected && shownHeartRate" class="text-white text-2xl">{{ heartRateValue }}</span>
        <button v-if="!isConnected && !shownHeartRate" @click="requestDevice">●</button>
    </div>
  </div>
</template>

<style>
@keyframes heart_scale {
  0% {
    transform: scale(0.9)
  }
  70% {
    transform: scale(1.03)
  }
  100% {
    transform: scale(0.9)
  }
}

.heart {
  animation: heart_scale 3s infinite;
}
</style>
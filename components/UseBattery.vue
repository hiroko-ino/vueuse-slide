<script setup lang="ts">
import { computed, reactive, ref } from 'vue'
import { useBattery, useInterval } from '@vueuse/core'

const props = defineProps({
    isUseModel: {
        type: Boolean,
        default: false
    }
})

const battery = reactive(useBattery())

const counter = useInterval(1500)

const batteryDemoValue = ref(100)

const interpolateColor = (color1: string, color2: string, ratio: number) => {
  // カラーコードを16進数からRGBに変換
  const r1 = parseInt(color1.substring(1, 3), 16);
  const g1 = parseInt(color1.substring(3, 5), 16);
  const b1 = parseInt(color1.substring(5, 7), 16);

  const r2 = parseInt(color2.substring(1, 3), 16);
  const g2 = parseInt(color2.substring(3, 5), 16);
  const b2 = parseInt(color2.substring(5, 7), 16);

  // ratioに基づいてカラーコードを補間
  const r = Math.round(r1 + (r2 - r1) * ratio);
  const g = Math.round(g1 + (g2 - g1) * ratio);
  const b = Math.round(b1 + (b2 - b1) * ratio);

  // RGBを16進数に変換してカラーコードを返す
  const hexR = r.toString(16).padStart(2, '0');
  const hexG = g.toString(16).padStart(2, '0');
  const hexB = b.toString(16).padStart(2, '0');
  return `#${hexR}${hexG}${hexB}`;
}

const getSkyColor = (value: number) => {
  if (value <= 40) {
    const ratio = value / 40;
    return interpolateColor('#746c88', '#ff974e', ratio);
  } else {
    const ratio = (value - 40) / 60;
    return interpolateColor('#ff974e', '#30a4f2', ratio);
  }
};

const getGdTopColor = (value: number) => {
  if (value <= 40) {
    const ratio = value / 40;
    return interpolateColor('#241b39', '#996971', ratio);
  } else {
    const ratio = (value - 40) / 60;
    return interpolateColor('#996971', '#1687d3', ratio);
  }
}

const getGdBottomColor = (value: number) => {
  if (value <= 40) {
    const ratio = value / 40;
    return interpolateColor('#c7b5c0', '#ffe142', ratio);
  } else {
    const ratio = (value - 40) / 60;
    return interpolateColor('#ffe142', '#a2d0ee', ratio);
  }
}

const batteryLevel = computed(() => props.isUseModel ? batteryDemoValue.value : battery.level * 100)

const baseColor = computed(() => getSkyColor(batteryLevel.value))
const gdTopColor = computed(() => getGdTopColor(batteryLevel.value))
const gdBottomColor = computed(() => getGdBottomColor(batteryLevel.value))

</script>

<template>
  <div class="wrapper">
    <div class="image" :style="{ backgroundColor: baseColor }">
      <div class="gd-top1" :style="{ backgroundColor: gdTopColor, opacity: 0.2 }"></div>
      <div class="gd-top2" :style="{ backgroundColor: gdTopColor, opacity: 0.2 }"></div>
      <div class="gd-top3" :style="{ backgroundColor: gdTopColor, opacity: 0.2 }"></div>
      <div class="gd-top4" :style="{ backgroundColor: gdTopColor, opacity: 0.2 }"></div>
      <div class="gd-bottom1" :style="{ backgroundColor: gdBottomColor, opacity: 0.2 }"></div>
      <div class="gd-bottom2" :style="{ backgroundColor: gdBottomColor, opacity: 0.2 }"></div>
      <div class="gd-bottom3" :style="{ backgroundColor: gdBottomColor, opacity: 0.2 }"></div>
      <div class="gd-bottom4" :style="{ backgroundColor: gdBottomColor, opacity: 0.2 }"></div>
      <img class="image__base" src="/use_battery/use_battery_background.png" alt="">
      <img class="sun" src="/use_battery/use_battery_sun.png" alt="" :style="{ position: 'absolute', top: `calc(4% + ${100 - batteryLevel} * 0.55%)`, right: '10%' }">
      <img class="moon" src="/use_battery/use_batterry_moon.png" alt="" :style="{ position: 'absolute', top: `calc(58% - ${100 - batteryLevel} * 0.55%)`, right: '10%', }">
      <div class="cloud cloud--1" :style="{ position: 'absolute', top: '5%', left: '6%', }">
        <img class="cloud__base" src="/use_battery/use_battery_cloud_01_base.png" alt="">
        <img class="cloud__gd1" src="/use_battery/use_battery_cloud_01_gd_01.png" alt="">
        <img class="cloud__gd2" src="/use_battery/use_battery_cloud_01_gd_02.png" alt="">
      </div>
      <div class="cloud cloud--2" :style="{ position: 'absolute', top: '24%', left: '25%', }">
        <img class="cloud__base" src="/use_battery/use_battery_cloud_02_base.png" alt="">
        <img class="cloud__gd1" src="/use_battery/use_battery_cloud_02_gd_01.png" alt="">
        <img class="cloud__gd2" src="/use_battery/use_battery_cloud_02_gd_02.png" alt="">
      </div>
      <img class="flower flower--1" src="/use_battery/use_battery_flower.png" alt="">
      <img class="flower flower--2" src="/use_battery/use_battery_flower.png" alt="">
      <img class="kuki" src="/use_battery/use_battery_kuki.png" alt="">
      <div class="dog">
        <div class="dog__pc">
          <img v-show="(counter % 2) === 0 && battery.charging" class="dog__ereki" src="/use_battery/use_battery_ereki_1.png" alt="">
          <img v-show="(counter % 2) !== 0 && battery.charging" class="dog__ereki" src="/use_battery/use_battery_ereki_2.png" alt="">
          <img v-show="battery.charging" class="dog__battery" src="/use_battery/use_battery_battery.png">
          <img v-show="(counter % 2) === 0" class="dog__mac" src="/use_battery/use_battery_dog_pc_1.png" alt="">
          <img v-show="(counter % 2) !== 0" class="dog__mac" src="/use_battery/use_battery_dog_pc_2.png" alt="">
        </div>
        <img class="dog__base" src="/use_battery/use_battery_dog_base.png" alt="">
        <img v-show="(counter % 2) === 0" class="dog__tail dog__tail--1" src="/use_battery/use_battery_dog_tail_1.png" alt="">
        <img v-show="(counter % 2) !== 0" class="dog__tail dog__tail--2" src="/use_battery/use_battery_dog_tail_2.png" alt="">
      </div>
    </div>
  </div>
  <div v-if="!battery.isSupported && !isUseModel" class="info">
    お使いのブラウザではAPIがサポートされていません
  </div>
  <div class="info" v-else-if="!isUseModel">
    デバイスが充電中かどうか: {{ battery.charging }}<br>
    現在の充電レベルを表す0～1の数値: {{ battery.level }}<br>
    デバイスが完全に充電されるまでの秒数:  {{ battery.chargingTime }}<br>
    デバイスが完全に放電されるまでの秒数: {{ battery.dischargingTime }}
  </div>
  <div v-else class="mt-2 flex justify-center">
    {{ batteryLevel }}
    <input type="range" v-model="batteryDemoValue" min="0" max="100">
  </div>
</template>

<style scoped>
@keyframes cloudAnime1 {
  0% {
    transform: translateX(0) translateY(0);
  }
  30% {
    transform: translateX(-7px) translateY(-5px);
  }
  60% {
    transform: translateX(5px) translateY(-7px);
  }
  100% {
    transform: translateX(0) translateY(0);
  }
}

@keyframes cloudAnime2 {
  0% {
    transform: translateX(0) translateY(0);
  }
  30% {
    transform: translateX(-12px) translateY(-7px);
  }
  60% {
    transform: translateX(3px) translateY(-5px);
  }
  100% {
    transform: translateX(0) translateY(0);
  }
}

@keyframes flower1 {
  0% {
    transform: translateX(0) translateY(0);
  }
  30% {
    transform: translateX(-3px) translateY(-2px) rotate(-4deg);
  }
  100% {
    transform: translateX(0) translateY(0);
  }
}

@keyframes flower2 {
  0% {
    transform: translateX(0) translateY(0);
  }
  30% {
    transform: translateX(-3px) translateY(-2px) rotate(-8deg);
  }
  100% {
    transform: translateX(0) translateY(0);
  }
}
.wrapper {
  text-align: center;
  padding-top: 0;
}
.image {
  margin-inline: auto;
  position: relative;
  overflow: hidden;
  width: 700px;
  max-width: 100%;
  border-radius: 16px;
}

.image__base {
  position: relative;
  z-index: 10;
  width: 100%;
  vertical-align: top;
}

.cloud {
  position: relative;
}

.cloud--1 {
  width: 21%;
  animation: cloudAnime1 11s infinite;
}

.cloud--2 {
  width: 10%;
  animation: cloudAnime2 11s infinite;
}

.cloud__base, .cloud__gd1, .cloud__gd2 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: auto;
}

.gd-bottom1 {
  position: absolute;
  bottom: 40%;
  left: 0;
  width: 100%;
  height: 27%;
}

.gd-bottom2 {
  position: absolute;
  bottom: 40%;
  left: 0;
  width: 100%;
  height: 22%;
}

.gd-bottom3 {
  position: absolute;
  bottom: 40%;
  left: 0;
  width: 100%;
  height: 16%;
}

.gd-bottom4 {
  position: absolute;
  bottom: 40%;
  left: 0;
  width: 100%;
  height: 12%;
}

.gd-top1 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 20%;
}

.gd-top2 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 16%;
}

.gd-top3 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 12%;
}

.info {
  text-align: center;
  font-family: 'DotGothic16', sans-serif;
  font-size: 16px;
  margin-top: 10px;
  font-weight: 700;
}

.sun {
  width: 10%;
  height: auto;
}

.moon {
  width: 6.7%;
  height: auto;
}

.flower {
  position: absolute;
  width: 12%;
  height: auto;
  z-index: 20;
}

.flower--1 {
  left: 3%;
  bottom: 5%;
  animation: flower1 infinite 4s;
}

.flower--2 {
  left: 7%;
  bottom: -5%;
  animation: flower2 infinite 4s;
}

.kuki {
  position: absolute;
  width: 10%;
  bottom: 0;
  left: 0;
  height: auto;
  z-index: 15;
}

.dog {
  position: absolute;
  top: 57%;
  left: 30%;
  z-index: 20;
  width: 19%;
}

.dog__base {
  width: 100%;
  height: auto;
  position: relative;
  z-index: 10;
}

.dog__tail {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 15;
}

.dog__pc {
  position: absolute;
  z-index: 5;
  width: 86%;
  top: 6%;
  left: -50%;
}

.dog__battery {
  position: absolute;
  bottom: 0;
  left: 16%;
  width: 30%;
}

.dog__mac {
  position: relative;
  z-index: 5;
  width: 96%;
  height: auto;
}

.dog__ereki {
  position: absolute;
  top: -20%;
  left: -8%;
  width: 100%;
  height: auto;
}
</style>

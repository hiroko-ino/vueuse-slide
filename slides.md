---
theme: none
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
title: v10.0突破記念、VueUseで手軽にWeb APIを触り、アイデアを実現しよう🥳
fonts:
  sans: 'Noto Sans JP'
---

# v10.0突破記念、<br>VueUseで手軽にWeb APIを触り、アイデアを実現しよう🥳

## + デモ on Slidev

2023/07/27<br>@Vue.jsの勉強会はなんぼあってもいいですからね<br>hiroko_ino

<style>
  .slidev-layout {
    background-color: #41B883;
    border-right: 20px solid #35495E;
    padding: 3rem 2rem 0 4rem;
    color: white;
  }
  h1 {
    font-size: 3rem;
    font-weight: 700;
  }
  h2 {
    margin-top: 0.8rem;
    font-size: 2rem;
    font-weight: 700;
  }
  p {
    text-align: right;
    margin-top: 6.7rem;
    font-size: 1.28rem;
  }
</style>

---
transition: slide-left
---

# 自己紹介

猪野 浩子 - hiroko_ino

<ul class="common-list">
  <li>9年間Web制作でデザインとエンジニアをしていて、昨年8月転職</li>
  <li>スポーツアプリの会社のフロントエンドエンジニア</li>
  <li>Vue.jsとFlutterを書いている</li>
</ul>

<ul class="sns-list">
  <li>
    <img src="/sns/twitter.png" alt="Twitter">
    @uribou_studying
  </li>
  <li>
    <img src="/sns/github.png" alt="GitHub">
    hiroko-ino
  </li>
  <li>
    <img src="/sns/zenn.svg" alt="Zenn">
    https://zenn.dev/hiroko_ino
  </li>
  <li>
    自作ブログ：https://type-any.com/
  </li>
</ul>

<img class="side" src="/uribou.jpg" alt="うりぼうくん">

<style>
.slidev-layout {
  padding: 2rem 2rem 2rem 0;
}

h1 {
  font-size: 2.8rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  line-height: 1;
}

h1::before {
  content: "";
  width: 1.5rem;
  height: 3px;
  background-color: #333;
  position: relative;
  top: 2px;
  margin-right: 0.5rem;
}

p {
  padding-left: 2.2rem;
  font-size: 2rem;
  margin-top: 2.5rem;
  font-weight: 700;
}

.common-list {
  margin-top: 1.48rem;
  padding-left: 2.2rem;
}

.common-list li {
  font-size: 1.7rem;
  line-height: 1.7;
}

.common-list li::before {
  content: "・";
}

.side {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  width: 13rem;
  height: 13rem;
}

.sns-list {
  margin-top: 2.5rem;
  padding-left: 2.2rem;
}

.sns-list li {
  font-size: 1.2rem;
  display: flex;
  align-items: center;
  line-height: 1.7;
}

.sns-list li img {
  height: 1.2rem;
  width: auto;
  margin-right: 0.8rem;
}
</style>

---
layout: index-page
---

# アジェンダ

- このスライドの説明
- VueUseとは
- VueUseで扱われているWeb APIとその関数紹介
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

---
layout: index-page
---

# アジェンダ

- **このスライドの説明**
- VueUseとは
- VueUseで扱われているWeb APIとその関数紹介
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

---
---

突然ですが、みなさん  

<style>
  .slidev-layout {
    background-color: #41B883;
    border-right: 20px solid #35495E;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  p {
    font-size: 3rem;
    font-weight: 700;
  }
</style>

---
---

ものづくり🔧のアイデアに  
困っていませんか？

<style>
  .slidev-layout {
    background-color: #41B883;
    border-right: 20px solid #35495E;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  p {
    font-size: 3rem;
    font-weight: 700;
  }
</style>

---
layout: common-page
---

# アイデアに困っているなら、VueUseが助けになるかもしれません

- VueUseはコンポーザブルな関数を200以上公開しています
- その中には実験的なWeb APIやEventを扱うもの、いろんな操作を便利にする独自の関数などがあります

関数一覧を眺めているだけで、アイデアが得られる！💪

<style>
  p {
    font-size: 1.7rem;
  }
</style>

---
layout: common-page
---

# 例えばこんなことが出来ます💡

useEyeDropper(EyeDropper API)とuseClipboard(Clipboard API)  
Vueファイルは35行（最小構成だと13行ほど）

<div class="w-130 m-auto relative">
  <ColorPicker />
</div>

<style>
  p {
    font-size: 1.5rem;
    margin-top: 1.3rem;
  }
</style>

---
---

このスライドは  
VueUseでWeb APIを触り、    
デモをするスライドです

<style>
  .slidev-layout {
    background-color: #41B883;
    border-right: 20px solid #35495E;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  p {
    font-size: 2.4rem;
    font-weight: 700;
  }
</style>

---
layout: common-page
---

# この登壇を見てくれた人に持ち帰ってもらえるとうれしいこと

- 自分もVueUseでなにか作ってみよう！の気持ち
- VueUseの便利さ
- 実験的なWeb APIの面白さ

---
transition: slide-left
---

# 本題の前に…

今回のライブデモはこちらでも見れます  

<style>
.slidev-layout {
  padding: 2rem 2rem 2rem 0;
}

h1 {
  font-size: 2.8rem;
  font-weight: 700;
  display: flex;
  align-items: center;
  line-height: 1;
}

h1::before {
  content: "";
  width: 1.5rem;
  height: 3px;
  background-color: #333;
  position: relative;
  top: 2px;
  margin-right: 0.5rem;
}

p {
  padding-left: 2.2rem;
  font-size: 2rem;
  margin-top: 2.5rem;
  font-weight: 700;
}
</style>

---
layout: index-page
---

# アジェンダ

- このスライドの説明
- **VueUseとは**
- VueUseで扱われているWeb APIとその関数紹介
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

---
layout: common-page-has-image
---

# VueUseとは？

<span>Collection of Vue Composition Utilities</span>  
コンポーザブルなユーティリティのコレクション

- 主にリアクティブな値（ref）を返すコンポーザブル関数を提供している
- 命名規則は主にuse〜
- 今お見せしているスライドの作成ツールSlidevでも、@vueuse/motionなどが使われています

![VueUse](/vueuse_logo.svg)

<style>
  .note {
    font-size: 1.3rem;
    color: #aaa;
  }
</style>

---
layout: common-page
---

# VueUseの利点

- **Feature Rich**🎛 : 200以上の関数を選べる
- **Seamless migration**🚀 : vue-demiをつかっているのでVue2, 3どちらでも動く（一部の関数に例外あり）
- **Fully tree shakeable**⚡ : パッケージから必要なコードのみを手に入れる
- **Type Strong**🦾 : TypeScriptで書かれ、完全なTSドキュメント付き
- **No bundler required**☁️ : CDNで使える
- **Interactive demos**🎪 : インタラクティブなデモも付き
- **Add-ons**🔌 : Router、Firebase、RxJSなど様々なアドオンをサポート。

...etc

<style>
  p {
    margin-top: 1rem;
  }

  li strong {
    color: #41B883;
  }
</style>

---
transition: slide-left
---

# Congratulation v10.0 Release!!🎉

![VueUse v10.0](/vueuse_v10.png)

<style>
.slidev-layout {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

h1 {
  padding-top: 1rem;
  padding-left: 1rem;
  font-size: 2rem;
  color: #41B883;
  font-weight: 700;
  text-align: center;
}

p {
  text-align: center;
}
</style>

---
layout: index-page
---

# アジェンダ

- このスライドの説明
- VueUseとは
- **VueUseで扱われているWeb APIとその関数紹介**
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

---
layout: common-page
---

# VueUseで扱われているWeb API（調べた限り）

- Web Bluetooth API ★ <span>Bluetooth通信</span>
- BroadcastChannel API <span>同じオリジンの閲覧コンテキスト通信</span>
- Clipboard API <span>クリップボード</span>
- EyeDropper API <span>スポイトツール</span>
- FileSystemAccessAPI <span>ローカルデバイス上のファイルなどを操作</span>
- Fullscreen API <span>フルスクリーン</span>
- Gamepad API <span>ゲームパッド</span>
- Permissions API <span>パーミッション</span>
- Screen Orientation API <span>現在の画面の向き</span>
- Web Share API <span>任意の共有ターゲットにコンテンツを共有する</span>
- Vibration API <span>振動させる</span>
- Screen Wake Lock API <span>端末が暗くならない</span>
- Battery Status API ★ <span>バッテリーステータス</span>
- Geolocation API <span>位置情報</span>
- SpeechRecognition <span>音声認識</span>
- SpeechSynthesis <span>合成音声</span>
- Web Animations API ★ <span>アニメーション</span>

<style>
  ul {
    display: flex;
    flex-wrap: wrap;
    gap: 10px 30px;
  }

  li {
    position: relative;
    font-weight: 700;
    font-size: 1.5rem;
  }

  li span {
    display: block;
    color: black;
    font-size: 0.8rem;
    text-indent: 0;
  }
</style>

---
---

<div>
  <h1># useBluetooth</h1>
  <p>VueUseでBluetooth通信を使う</p>
</div>

<style>
  .slidev-layout {
    background-color: #41B883;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  h1 {
    font-size: 3rem;
    font-weight: 700;
  }

  p {
    margin-top: 1rem;
    font-size: 1.8rem;
    font-weight: 700;
  }
</style>

---
layout: common-page
---

# useBluetooth

<table>
  <tr>
    <th>Package</th>
    <td>@vueuse/core</td>
  </tr>
  <tr>
    <th>API</th>
    <td>Web Bluetooth API</td>
  </tr>
  <tr>
    <th>API Description</th>
    <td>Web Bluetooth APIは、Bluetooth Low Energy周辺機器に接続し、相互作用する機能を提供します。<br>Bluetooth Low Energy(BLE)は、Bluetooth4.0で追加された規格</td>
  </tr>
  <tr>
    <th>Support</th>
    <td>ChromeとEdgeがPartial Support、Android ChromeがFull support</td>
  </tr>
  <tr>
    <th>Parameter</th>
    <td>requestDevice()のオプションのfilters, optionalServices, acceptAllDevicesを受け取る<br>(カスタムのnavigatorインスタンスを渡すことも可)</td>
  </tr>
  <tr>
    <th>Object</th>
    <td>navigator.bluetooth</td>
  </tr>
</table>

---
layout: common-page-code
---

# Usage

```ts
import { useBluetooth } from '@vueuse/core'

const {
  isSupported, // サポートされているか navigator && 'bluetooth' in navigator
  isConnected, // BLEデバイスと繋がっているか
  device, // 接続したデバイス
  requestDevice, // navigator?.bluetooth.requestDevice()
  server, // device.gatt.connect()の返り値
  error, // エラーオブジェクト
} = useBluetooth({
  acceptAllDevices: true,
})
```

---
layout: common-page
---

# 活用方法

- スマートウォッチのバッテリーレベルを読み取る
- 温度などのセンサーデータの取得
- BLEデバイスでサポートされるサービスを確認する
- LEDの色を更新する etc...

<style>
  p {
    font-size: 1.6rem;
  }
</style>

---
---

みなさま  
お気づきでしょうか

<style>
  .slidev-layout {
    background-color: #41B883;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  p {
    font-size: 3rem;
    font-weight: 700;
  }
</style>

---
---

これ 👉

<style>
  .slidev-layout {
    background-color: #41B883;
    color: white;
  }

  p {
    position: absolute;
    top: 1rem;
    right: 6.5rem;
    font-size: 3rem;
    font-weight: 700;
  }
</style>

---
---

心拍数を表示する  
配信者スタイルで  
これからお届けします

<style>
  .slidev-layout {
    display: grid;
    place-items: center;
    text-align: center;
  }

  p {
    font-size: 2.4rem;
    font-weight: 700;
  }
</style>

---
layout: common-page-code
---

# こちらのコード(1/3)

```ts
import { pausableWatch, useBluetooth } from '@vueuse/core'
import { ref } from 'vue';

...

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

```

<style>
  .slidev-code {
    height: 60vh !important;
    overflow-y: scroll;
  }
</style>

---
layout: common-page-code
---

# こちらのコード(2/3)

```ts
...
const getHeartRate = async () => {
  isGettingHeartRate.value = true
  if (!server.value) return
  const heartRateService = await server.value.getPrimaryService('heart_rate')
  const heartRateCharacteristic = await heartRateService.getCharacteristic(
    'heart_rate_measurement',
  )
  heartRateCharacteristic.startNotifications();
  heartRateCharacteristic.addEventListener('characteristicvaluechanged', (event) => {
    const value = event.target.value
    if (value.getUint8(0) & 0x01) {
      heartRateValue.value = value.getUint16(1, /*littleEndian=*/true)
    } else {
      heartRateValue.value = value.getUint8(1)
}})}
```

<style>
  .slidev-code {
    height: 60vh !important;
    overflow-y: scroll;
  }
</style>

---
layout: common-page-code
---

# こちらのコード(3/3)

```ts
...
const { stop } = pausableWatch(isConnected, (newIsConnected) => {
  if (!newIsConnected || !server.value || isGettingHeartRate.value) return
  getHeartRate()
  stop()
})

...テンプレートとスタイルの記述が続く
```

<style>
  .slidev-code {
    height: 60vh !important;
    overflow-y: scroll;
  }
</style>


---
layout: common-page
---

# VueUseで扱う利点とサマリ

- マウント時に接続、アンマウント時に切断を請け負ってくれる
- isSupportedとエラーオブジェクトの返却
- （全関数共通として）コンポーネント側はシンプルになる

https://googlechrome.github.io/samples/web-bluetooth/index.html  
にサンプルが色々あり、これをVue（VueUse）に直して見るだけでもアウトプットになりそう👀

<style>
  p {
    font-size: 1.6rem;
    font-weight: 400;
  }
</style>

---
---

<div>
  <h1># useBattery</h1>
  <p>VueUseでBattery Status APIを扱う</p>
</div>

<style>
  .slidev-layout {
    background-color: #41B883;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  h1 {
    font-size: 3rem;
    font-weight: 700;
  }

  p {
    margin-top: 1rem;
    font-size: 1.8rem;
    font-weight: 700;
  }
</style>

---
layout: common-page
---

# useBattery

<table>
  <tr>
    <th>Package</th>
    <td>@vueuse/core</td>
  </tr>
  <tr>
    <th>API</th>
    <td>Battery Status API</td>
  </tr>
  <tr>
    <th>API Description</th>
    <td>バッテリー状態 API は、 バッテリー API と呼ばれることの方が多いのですが、システムのバッテリー充電レベルに関する情報の提供、およびバッテリーレベルや充電状態が変化したときに発生するイベントによる通知を可能にします。(MDN日本語より)</td>
  </tr>
  <tr>
    <th>Support</th>
    <td>ChromeとEdgeとAndroid ChromeがFull support</td>
  </tr>
  <tr>
    <th>Parameter</th>
    <td>カスタムのnavigatorインスタンスを渡すことが出来る</td>
  </tr>
  <tr>
    <th>Object</th>
    <td>navigator.getBattery</td>
  </tr>
</table>

---
layout: common-page-code
---

# Usage

```ts
import { useBattery } from '@vueuse/core'

const {
  charging, // チャージ中かどうかのboolean
  chargingTime, // デバイスが完全に充電されるまでの秒数
  dischargingTime, // デバイスが完全に放電されるまでの秒数
  level // 現在の充電レベルを表す0～1の数値
} = useBattery()
```

<style>
  p {
    margin-top: 1rem;
    padding-left: 2.2rem;
    font-size: 1.6rem;
  }
</style>

---
---

作ってみよう：  
充電レベルに応じて変わる絵🖼

<style>
  .slidev-layout {
    background-color: #41B883;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  p {
    font-size: 3rem;
    font-weight: 700;
  }
</style>

---
---

<UseBattery />

<style>
.slidev-layout {
  padding-top: 1rem;
}
</style>

---
layout: common-page-code
---

# こちらのコード(1/3)

```ts
import { computed, reactive, ref } from 'vue'
import { useBattery, useInterval } from '@vueuse/core'

const battery = reactive(useBattery())

const counter = useInterval(1500) // ミリ秒ごとにカウントアップ

...続く
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

---
layout: common-page-code
---

# こちらのコード(2/3)

```ts
...
// ChatGPTに考えてもらった色変換
const interpolateColor = (color1: string, color2: string, ratio: number) => {
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
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

---
layout: common-page-code
---

# こちらのコード(2/3)

```ts
...
const getSkyColor = (value: number) => {
  if (value <= 40) {
    const ratio = value / 40;
    return interpolateColor('#746c88', '#ff974e', ratio);
  } else {
    const ratio = (value - 40) / 60;
    return interpolateColor('#ff974e', '#30a4f2', ratio);
  }
};

...色取得を必要な分繰り返す

const batteryLevel = computed(() => battery.level * 100)
// 色を必要な分計算する
const baseColor = computed(() => getSkyColor(batteryLevel.value))
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>


---
layout: common-page
---

# VueUSeの利点とサマリ

- 値がリアクティブでUIの更新がしやすい
- 内部的にVueUseのuseEventListenerを使っているのでアンマウント時にListenerを解除
- （全関数共通として）コンポーネント側はシンプルになる

Chromiumでしか使えないのは難点ですが、バッテリーレベルに応じてダークモードにするなどに使っていけるかもしれません

<style>
  p {
    font-size: 1.6rem;
    font-weight: 400;
  }
</style>

---
---

<div>
  <h1># useAnimate</h1>
  <p>VueUseでWeb Animations APIを扱う<br>v10.0から追加された関数🎉</p>
</div>

<style>
  .slidev-layout {
    background-color: #41B883;
    color: white;
    display: grid;
    place-items: center;
    text-align: center;
  }

  h1 {
    font-size: 3rem;
    font-weight: 700;
  }

  p {
    margin-top: 1rem;
    font-size: 1.8rem;
    font-weight: 700;
  }
</style>

---
layout: common-page
---

# useAnimate

<table>
  <tr>
    <th>Package</th>
    <td>@vueuse/core</td>
  </tr>
  <tr>
    <th>API</th>
    <td>Web Animations API</td>
  </tr>
  <tr>
    <th>API Description</th>
    <td>ウェブアニメーション API により、JavaScript でアニメーションを構築したり、再生を制御したりすることができます。(MDN日本語より)</td>
  </tr>
  <tr>
    <th>Support</th>
    <td>PCモダンブラウザとChrome for AndroidはFull Support、 Safari on iOSはcomposite modeがサポートされていない</td>
  </tr>
  <tr>
    <th>Object</th>
    <td>Element.animate</td>
  </tr>
</table>

<style>
  p {
    font-size: 1.8rem;
    margin-top: 1rem;
  }
</style>

---
layout: common-page-code
---

# Usage

```ts
const el = ref()
const {
  isSupported, // サポートされているか
  animate, // Animationオブジェクト

  // actions
  play, // 再生する
  pause, // 中止する
  reverse, // 逆再生に切り替える
  finish, // 完了する
  cancel, // キャンセルする

  // states
  pending, // 再生待ちや再生中の一時停止などの非同期操作を待機しているか
  playState, // アニメーションの再生状態を示す列挙値
  replaceState, // アニメーションの置換状態を返す
  startTime, // アニメーションの再生が始まる予定の時刻を取得または設定
  currentTime, // このアニメーションの現在時刻の値
  timeline, // このアニメーションに関連付けられる timeline (en-US) を取得または設定する
  playbackRate, // このアニメーションの再生速度を取得または設定する
} = useAnimate(el, { transform: 'rotate(360deg)' }, 1000)
```

<style>
  .slidev-code {
    font-size: 0.8rem !important;
  }
</style>

---
---

<UseAnimate />

---
layout: common-page-code
---

# こちらのコード

```ts {all}{ lines: true }
import { shallowRef } from 'vue'
import { useAnimate, type MaybeElement } from '@vueuse/core'

// export type MaybeElement = HTMLElement | SVGElement | VueInstance | undefined | null
const el = shallowRef<MaybeElement>()

const {
  play,
  pause,
  reverse,
  finish,
  cancel,
  startTime,
  currentTime,
  playbackRate,
  playState,
  replaceState,
  pending,
} = useAnimate(
  el,
  [
    { clipPath: 'circle(8% at 70% 30%)' },
    { clipPath: 'circle(25% at 50% 90%)' },
    { clipPath: 'circle(3% at 100% 30%)' },
    { clipPath: 'circle(15% at 40% 70%)' },
  ],
  {
    duration: 6000,
    iterations: 5,
    direction: 'alternate',
    easing: 'cubic-bezier(0.46, 0.03, 0.52, 0.96)',
  },
)
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

---
layout: common-page
---

# VueUSeの利点とサマリ

- 値がリアクティブでUIの更新がしやすい
- isSupported
- マウント時に再設定、アンマウント時にキャンセルを行う
- （全関数共通として）コンポーネント側はシンプルになる

Chromiumでしか使えないのは難点ですが、バッテリーレベルに応じてダークモードにするなどに使っていけるかもしれません

<style>
  p {
    font-size: 1.6rem;
    font-weight: 400;
  }
</style>

---
layout: common-page
---

# 他にも関数はたくさん！

- Web API関連の他にも、Event関連や様々なAdd-onもあるので是非みなさんも使ってください🤗
  - @vueuse/gesture, @vueuse/sound ...etc
- VueUseはコンポーザブル関数の集まりなので、関数1ファイルで結構把握出来るのでちょっとしたOSSコードリーディングにもおすすめ
  - ただ、現在新しい関数の受け付けはスローダウンしているようなので、コントリビューションは気をつけよう

---
layout: common-page-has-image
---

# まとめ

- VueUseの関数はアイデアの宝庫
- VueUseを使ったことがない方にもちょっとでも興味をもってもらえると嬉しい
- 実験的なWeb APIを扱ってくれているVueUseに感謝🙏

![うりぼうくん](/uribou_nemuri.png)

---
---

![おわり](/end.png)
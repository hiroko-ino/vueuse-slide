---
theme: none
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
title: v10.0突破記念！VueUseで手軽にWeb APIを実験してみよう🥳
fonts:
  sans: 'Noto Sans JP'
---

# v10.0突破記念！<br>VueUseで手軽にWeb APIを<br>実験してみよう🥳

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

<!--
はい、それではv10.0突破記念！VueUseで手軽にWeb APIを実験してみよう🥳という題で登壇させていただきます、よろしくお願いします
-->

---
transition: slide-left
---

# 自己紹介

猪野 浩子 - hiroko_ino

<ul class="common-list">
  <li>9年間Web制作でデザイナーとエンジニアをし、昨年8月転職してスポーツアプリの会社でVue.jsとFlutterを書いている</li>
  <li>湘南に生息</li>
  <li>VueUseとSlidevが好き</li>
</ul>

<ul class="sns-list">
  <li>
    <a href="https://twitter.com/uribou_studying" target="_blank">
      <img src="/sns/twitter.png" alt="Twitter">
      @uribou_studying
    </a>
  </li>
  <li>
    <a href="https://github.com/hiroko-ino" target="_blank">
      <img src="/sns/github.png" alt="GitHub">
      hiroko-ino
    </a>
  </li>
  <li>
    <a href="https://zenn.dev/hiroko_ino" target="_blank">
      <img src="/sns/zenn.svg" alt="Zenn">
      https://zenn.dev/hiroko_ino
    </a>
  </li>
  <li>
    ブログ：
    <a href="https://type-any.com/" target="_blank">
      https://type-any.com/
    </a>
  </li>
</ul>

<img class="side side--l" src="/profile.jpg" alt="リアル写真">
<img class="side side--r" src="/uribou.jpg" alt="うりぼうくん">

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
  font-size: 1.5rem;
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

.side {
  position: absolute;
}

.side--l {
  width: 13rem;
  height: 13rem;
  right: 2rem;
  bottom: 1rem;
  border-radius: 16px;
}

.side--r {
  width: 7rem;
  height: 7rem;
  right: 11rem;
  bottom: 10rem;
  border-radius: 50%;
  border: 3px solid #eee;
}

.sns-list {
  margin-top: 2.5rem;
  padding-left: 2.2rem;
}

.sns-list li {
  font-size: 1.2rem;
  line-height: 1.7;
}

.sns-list li a {
  display: inline-flex;
  align-items: center;
  text-decoration: underline;
}

.sns-list li img {
  height: 1.2rem;
  width: auto;
  margin-right: 0.8rem;
}
</style>

<!--
自己紹介します
猪野と申します、SNS類は本名そのままのhiroko_inoという名前でやっています。
9年間web制作でデザイナーとエンジニアをやっていて、去年8月に転職して今はスポーツアプリの会社でVue.jsとFlutterを書いています。
湘南に生息しています。
VueUseとSlidevが好きです。
-->

---
layout: index-page
---

# アジェンダ

- 今日伝えたいこと
- VueUseとは
- VueUseで扱われているWeb APIとその関数紹介
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

<!--
アジェンダはこのようになります。
-->

---
layout: index-page
---

# アジェンダ

- **今日伝えたいこと**
- VueUseとは
- VueUseで扱われているWeb APIとその関数紹介
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

<!--
今日伝えたいことです。
-->

---
---

みなさん、VueUse  
使ったことありますか？

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

<!--
みなさん、VueUse使ったことありますか？
-->

---
layout: common-page
---

# VueUseには、たくさんの関数があります

- VueUseはコンポーザブルな関数の集合
- 関数を200以上公開しています
- その中には実験的なWeb APIやEventを扱うもの、いろんな操作を便利にする独自の関数などがあります

<style>
  p {
    font-size: 1.7rem;
  }
</style>

<!--
VueUseには、たくさんの関数があります。
VueUseはコンポーザブルな関数の集合です。
関数を200以上公開しています。
その中には実験的なWeb APIやEventを扱うもの、色んな操作を便利にする独自の関数などがあります。
-->

---
layout: common-page
---

# 今日の内容は、VueUse × Web API
 
- VueUseの関数から様々な（実験的含む）Web APIを知ることが出来る   
- Slidev上でデモし、デモのコードを公開します
- VueUseの実際のコードや、内部で扱われている関数、便利さを学びます

今回はサードパーティ API（普段アプリケーション開発でサーバーから叩いているもの）の話はありません🙅‍♀🙇‍♀️

<style>
  p {
    font-size: 1.7rem;
  }
</style>

<!--
今日の登壇はVueUseの中でWeb APIを扱うものを取り上げます。

VueUseのたくさんの関数の中から、実験的含むWeb APIを扱う関数をピックアップし、Web APIと内部で扱われている関数を速習します。

Vueコンポーネントが使えるSlidev上でデモをします。

今回は、サードパーティAPI、普段アプリケーション開発でサーバーから叩いているものの話はありません。
-->

---
layout: common-page
---

# 例えばこんなことが出来ます💡

useEyeDropper(EyeDropper API)とuseClipboard(Clipboard API)  
Vueファイルは35行（スタイル等なし最小構成だと13行ほど）

<div class="w-130 m-auto relative">
  <ColorPicker />
</div>

<style>
  p {
    font-size: 1.5rem;
    margin-top: 1.3rem;
  }
</style>

<!--
例えばこのようなことが出来るという例で、useEyeDropperというEyeDropper APIを扱う関数と、useClipboardというClipboard APIを扱う関数を使い、このようなカラーコードをコピーできるカラーピッカーが作れます。こちらはVueファイルが35行ほどで、スタイルなし最小構成だと13行ほどになります。
-->

---
layout: common-page
---

# 本日持ち帰ってほしいこと🐤

- 自分もVueUseでなにか作ってみよう！の気持ち
- VueUseの便利さ、VueUseへの興味
- 実験的なWeb APIの面白さ

<!--
本日持ち帰ってほしいことはこのようになっています。
- 自分もVueUseでなにか作ってみよう！の気持ち
- VueUseの便利さ、VueUseへの興味
- 実験的なWeb APIの面白さ
です。
-->

---
transition: slide-left
---

# 本題の前に…

今回のデモはこちらでも見れます  
<a href="https://hiroko-ino.github.io/7_27_vue_slide_entrance/" target="_blank">https://hiroko-ino.github.io/7_27_vue_slide_entrance/</a>

<img class="mt-10 block m-auto" src="/qr.png" alt="QRコード">

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

<!--
本題の前に、今回のデモはこちらでも見れます。
QRコードを読み取りたい方のために今から15秒ほど待ちます。
ツイッターでもこちらのリンクをツイートしていますので、そちらから辿っていただくほうがいいかもしれません。私のTwitterはconnpassページから飛べるようになっているはずです。（少し待つ）
-->

---
layout: index-page
---

# アジェンダ

- 今日伝えたいこと
- **VueUseとは**
- VueUseで扱われているWeb APIとその関数紹介
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

<!--
それでは、VueUseとはに移っていきます
-->

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

<!--
VueUseとは、Collection of Vue Composition Utilities（ゆっくり話す）、つまりコンポーザブルなユーティリティのコレクションです。
主にリアクティブなrefを返すコンポーザブル関数を提供しています。
命名規則は慣例に則ってuseほにゃららが主となっています。
今お見せしているスライドを作成したツールSlidevでも、@vueuse/motionなどが使われています
-->

---
layout: common-page
---

# VueUseの利点

- **Feature Rich**🎛 : 200以上の関数が選べる
- **Seamless migration**🚀 : Vue3と2で使えます
- **Fully tree shakeable**⚡ : パッケージから必要なコードのみを手に入れる
- **Type Strong**🦾 : TypeScriptで書かれ、完全なTSドキュメント付き
- **No bundler required**☁️ : CDNで使える
- **Interactive demos**🎪 : インタラクティブなデモも付き
- **Add-ons**🔌 : Router、Firebase、RxJSなど様々なアドオンをサポート

...etc

<style>
  p {
    margin-top: 1rem;
  }

  li strong {
    color: #41B883;
  }
</style>

<!--
VueUseの利点としては、200以上の関数が選べることと、vue-demiというライブラリが使われているので一部関数を除きVue3、2どちらの環境でも使えること、Tree Shakableなのでほしいコードのみを手に入れることが出来ること、多彩なデモが公式サイトで見れることなどがあります。
-->

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

<!--
VueUseは4月頃にv10.0がリリースされています。今回は、v10.0で新しく追加された関数も紹介していきますので、お楽しみにしていてください。
-->

---
layout: index-page
---

# アジェンダ

- 今日伝えたいこと
- VueUseとは
- **VueUseで扱われているWeb APIとその関数紹介**
  - デモ
  - コード紹介
  - VueUseを使う利点
- おわりに

<!--
それでは、VueUseで扱われているWeb APIとその関数紹介に移っていきます。
-->

---
layout: common-page
---

# VueUseで扱われているWeb API（調べた限り）

- <span class="color">Web Bluetooth API ★</span> <span class="note">Bluetooth通信</span>
- BroadcastChannel API <span class="note">同じオリジンの閲覧コンテキスト通信</span>
- Clipboard API <span class="note">クリップボード</span>
- EyeDropper API <span class="note">スポイトツール</span>
- FileSystemAccessAPI <span class="note">ローカルデバイス上のファイルなどを操作</span>
- Fullscreen API <span class="note">フルスクリーン</span>
- Gamepad API <span class="note">ゲームパッド</span>
- Permissions API <span class="note">パーミッション</span>
- Screen Orientation API <span class="note">現在の画面の向き</span>
- Web Share API <span class="note">>任意の共有ターゲットにコンテンツを共有する</span>
- Vibration API <span class="note">振動させる</span>
- Screen Wake Lock API <span class="note">端末が暗くならない</span>
- <span class="color">Battery Status API ★</span> <span class="note">バッテリーステータス</span>
- Geolocation API <span class="note">位置情報</span>
- SpeechRecognition <span class="note">音声認識</span>
- SpeechSynthesis <span class="note">合成音声</span>
- <span class="color">Web Animations API ★</span> <span class="note">アニメーション</span>

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

  li span.note {
    display: block;
    color: inherit;
    font-size: 0.8rem;
    text-indent: 0;
  }
</style>

<!--
VueUseで扱われている関数は調べた限りではこれくらいあります。今回は、この中で星マークをつけているものをピックアップして紹介していきます。
-->

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

<!--
それでは、useBluetoothの紹介です。
-->

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
</table>

<!--
useBluetoothはWeb Bluetooth APIを扱う関数です。Web Bluetooth APIは、Bluetooth Low EnergyというBluetooth4.0で追加された規格の機器に接続するAPIです。
サポートしてはChromeとEdgeがPartial Support、Android ChromeがFull supportです。
-->

---
layout: common-page-code
---

# 使い方

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

<!--
使い方としてはこのようになっています。
Web Bluetooth APIがサポートされているかどうかの変数や、接続されているか、デバイスオブジェクト、サーバーオブジェクトなどが返却されます。
useBluetoothの引数には、基本的にnavigator?.bluetooth.requestDeviceにわたすオプションと同様のものをわたします。
-->

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

<!--
活用例としてはこのようになっています。
Qiitaにかなり記事がありますので、興味のある方は是非記事検索してみてください。
-->

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

<!--
みなさま、お気づきでしょうか
-->

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

<!--
こちら気になっていましたでしょうか。
はい、お察しの方もいらっしゃるかもしれませんが、こちら、セキュリティの観点から事前にペア設定していましたが、私の左腕につけている心拍センサーから心拍数を取っています。こちらで表示非表示できるのですが、はい、私の心拍数が表示されています。これで私の緊張感をみなさんに共有できますね。なんだか海外のRTA走者になった気分ですね。
-->

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

<!--
それでは、心拍数を表示する配信者スタイルでこれからお届けします。
-->

---
layout: common-page-code
---

# こちらのコード(1/3)

```ts
import { pausableWatch, useBluetooth } from '@vueuse/core'
import { ref } from 'vue';

const heartRateValue = ref<undefined | number>(0)
const isGettingHeartRate = ref(false)

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
...
```

<style>
</style>

<!--
実際のコードはこのような感じになっています。まずはuseBluetoothの呼び出しですが、ペア設定要求時に表示されるデバイスを限定しない書き方にしています。
-->

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

<!--
getHeartRateという関数で、serverオブジェクトからの操作を行います。
このあたりの操作に関しては、useBluetoothを使っても簡略化されない部分ですね。
characteristicvaluechangedのEventのListenerを登録して、変更値を受け取ったら心拍数が更新されるようになっています。
-->

---
layout: common-page-code
---

# こちらのコード(3/3)

```ts
...
// 返り値としてstop（watchを止める関数）を得られるVueUseの関数
const { stop } = pausableWatch(isConnected, (newIsConnected) => {
  if (!newIsConnected || !server.value || isGettingHeartRate.value) return
  getHeartRate()
  stop()
})

...テンプレートとスタイルの記述が続く
```

<!--
ここでVueUseのpausableWatchというのが出てきます。これはwatchの返り値として、stop, pause, resumeを受け取ります。この場合は、isConnectedが新しくtrueになった場合に、getHeartRateを呼び出し、watchを止めています。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
...
watch(device, () => {
  connectToBluetoothGATTServer()
})

async function requestDevice(): Promise<void> {
  ...
  try {
    device.value = await navigator?.bluetooth.requestDevice({
      acceptAllDevices,
      filters,
      optionalServices,
    })
  }
  catch (err) {
    error.value = err
  }
}
```

<!--
VueUse本体のコードです。デバイスをwatchしてBluetoothのサーバーと接続する関数を実行します。
navigator.bluetooth.requestDeviceをtryで行い、エラーの場合エラーオブジェクトを保存します。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
...
async function connectToBluetoothGATTServer() {
  // Reset any errors we currently have:
  error.value = null

  if (device.value && device.value.gatt) {
    // Add callback to gattserverdisconnected event:
    device.value.addEventListener('gattserverdisconnected', () => {})

    try {
      // Connect to the device:
      server.value = await device.value.gatt.connect()
    }
    catch (err) {
      error.value = err
    }
  }
}
```

<!--
deviceのwatchから呼んでいた関数はこちらです。
ここでserverオブジェクトを返却用のrefに代入しています。
-->
---
layout: common-page-code
---

# VueUse本体のコード

```ts
...
// 安全なonMounted。コンポーネントのライフサイクルの中にある場合はonMounted()を呼び出します
tryOnMounted(() => {
  if (device.value)
    device.value.gatt?.connect()
})

// 安全な onScopeDispose。エフェクト・スコープのライフサイクルの中にあればonScopeDispose()を呼び出す。
tryOnScopeDispose(() => {
  if (device.value)
    device.value.gatt?.disconnect()
})
...
```

<!--
ここでtryOnMountedとtryOnScopeDisposeが出てきます。これもVueUseの関数です。
tryOnMountedはコンポーネントのライフサイクルの中にある場合はonMounted()はを呼び出します。
tryOnScopeDisposeはエフェクト・スコープのライフサイクルの中にあればonScopeDispose()を呼び出します。
これを見ると、マウント時に接続、アンマウント時に切断をしてくれているようですね。
-->

---
layout: common-page-code
---

# 素で書こうとするとこれくらいの複雑さ

```ts
var bluetoothDevice;
var batteryLevelCharacteristic;

async function onReadBatteryLevelButtonClick() {
  try {
    if (!bluetoothDevice) {
      await requestDevice();
    }
    await connectDeviceAndCacheCharacteristics();

    log('Reading Battery Level...');
    await batteryLevelCharacteristic.readValue();
  } catch(error) {
    log('Argh! ' + error);
  }
}

async function requestDevice() {
  log('Requesting any Bluetooth Device...');
  bluetoothDevice = await navigator.bluetooth.requestDevice({
   // filters: [...] <- Prefer filters to save energy & show relevant devices.
      acceptAllDevices: true,
      optionalServices: ['battery_service']});
  bluetoothDevice.addEventListener('gattserverdisconnected', onDisconnected);
}

async function connectDeviceAndCacheCharacteristics() {
  if (bluetoothDevice.gatt.connected && batteryLevelCharacteristic) {
    return;
  }

  log('Connecting to GATT Server...');
  const server = await bluetoothDevice.gatt.connect();

  log('Getting Battery Service...');
  const service = await server.getPrimaryService('battery_service');

  log('Getting Battery Level Characteristic...');
  batteryLevelCharacteristic = await service.getCharacteristic('battery_level');

  batteryLevelCharacteristic.addEventListener('characteristicvaluechanged',
      handleBatteryLevelChanged);
  document.querySelector('#startNotifications').disabled = false;
  document.querySelector('#stopNotifications').disabled = true;
}

/* This function will be called when `readValue` resolves and
 * characteristic value changes since `characteristicvaluechanged` event
 * listener has been added. */
function handleBatteryLevelChanged(event) {
  let batteryLevel = event.target.value.getUint8(0);
  log('> Battery Level is ' + batteryLevel + '%');
}

async function onStartNotificationsButtonClick() {
  try {
    log('Starting Battery Level Notifications...');
    await batteryLevelCharacteristic.startNotifications();

    log('> Notifications started');
    document.querySelector('#startNotifications').disabled = true;
    document.querySelector('#stopNotifications').disabled = false;
  } catch(error) {
    log('Argh! ' + error);
  }
}

async function onStopNotificationsButtonClick() {
  try {
    log('Stopping Battery Level Notifications...');
    await batteryLevelCharacteristic.stopNotifications();

    log('> Notifications stopped');
    document.querySelector('#startNotifications').disabled = false;
    document.querySelector('#stopNotifications').disabled = true;
  } catch(error) {
    log('Argh! ' + error);
  }
}

function onResetButtonClick() {
  if (batteryLevelCharacteristic) {
    batteryLevelCharacteristic.removeEventListener('characteristicvaluechanged',
        handleBatteryLevelChanged);
    batteryLevelCharacteristic = null;
  }
  // Note that it doesn't disconnect device.
  bluetoothDevice = null;
  log('> Bluetooth Device reset');
}

async function onDisconnected() {
  log('> Bluetooth Device disconnected');
  try {
    await connectDeviceAndCacheCharacteristics()
  } catch(error) {
    log('Argh! ' + error);
  }
}
```

<style>
  .slidev-code {
    height: 60vh !important;
    overflow-y: scroll;
  }
</style>

<!--
サッと紹介するのですが、素で使おうとするとこれくらい複雑です。これに加えてアンマウントの処理をいれなければなりません。
-->

---
layout: common-page
---

# VueUseで扱う利点とまとめ

- マウント時に接続、アンマウント時に切断を請け負ってくれる
- isSupportedとエラーオブジェクトの返却

https://googlechrome.github.io/samples/web-bluetooth/index.html  
にサンプルが色々あり、これをVue（VueUse）に直して見るだけでもアウトプットになりそう👀

<style>
  p {
    font-size: 1.6rem;
    font-weight: 400;
  }
</style>

<!--
VueUseで扱う利点とまとめです。

マウント時に接続、アンマウント時に切断を請け負ってくれます
isSupportedとエラーオブジェクトの返却

https://googlechrome.github.io/samples/web-bluetooth/index.html  
にサンプルが色々あり、これをVue（VueUse）に直して見るだけでもアウトプットになりそうかなと思っています👀
-->

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

<!--
次は、useBatteryの紹介です
-->

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
</table>

<!--
useBatteryはBattery Status APIを扱います。Battery Status APIはバッテリーの充電レベルに関する情報の提供を行います。
ChromeとEdgeとAndroid ChromeがFull supportとなっています。
-->

---
layout: common-page-code
---

# 使い方

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

<!--
使い方としてはこのようになっています。
各充電レベルに関する情報がリアクティブに受け取れます。
-->

---
---

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

<!--
一つ、作ってみたということで、充電レベルに応じて変わる絵になります。
-->

---
---

<UseBattery />

<style>
.slidev-layout {
  padding-top: 1rem;
}
</style>

<!--
こちらがその実際のライブデモです。
充電中かどうか、充電レベルの数値、完全に充電されるまでの秒数、完全に放電されるまでの時間を取得しています。充電レベルに応じて空の色が変わるのと、充電されているかどうかでも絵が変わります。Chrome系でデモのURLをご覧になっている方は、是非どんな景色が広がっていたのか教えてください。
-->

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

<!--
こちらのコードはこのようになります。まずはuseBatteryを呼び出します。
useIntervalというVueUseの関数を使っていて、こちらは引数のミリ秒ごとにカウントアップして、これを交互にpng画像を切り替えるのに使っています。
-->

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

<!--
充電レベルからの色変換はChatGPTにコードを考えてもらいました。グラデーションを作りたい2つのカラーコードと、充電レベルをわたします。
少しスクロールしますね。
-->

---
layout: common-page-code
---

# こちらのコード(3/3)

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

<!--
これを各computedで計算します。
バッテリーレベルに関しては、使いやすいように100をかけています。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
...（export function useBatteryの中身）
  function updateBatteryInfo(this: BatteryManager) {
    charging.value = this.charging
    chargingTime.value = this.chargingTime || 0
    dischargingTime.value = this.dischargingTime || 0
    level.value = this.level
  }

  if (isSupported.value) {
    (navigator as NavigatorWithBattery)
      .getBattery()
      .then((_battery) => {
        battery = _battery
        updateBatteryInfo.call(battery)
        for (const event of events)
          useEventListener(battery, event, updateBatteryInfo, { passive: true })
      })
  }
...
```

<!--
VueUse本体のコードです。
useBatteryの中には、updateBatteryInfoという値をリアクティブに更新する関数があり、それらをuseEventListenerをつかって設定しています。useEventListenerはVueUse頻出の関数で、マウント時にaddEventListener、アンマウント時にremoveEventListenerを自動でしてくれます。VueUse全体として、マウント時とアンマウント時のやりくりを請け負ってくれるのが特徴ですね。
-->

---
layout: common-page-code
---

# 素で書こうとするとこれくらいの複雑さ

```ts
navigator.getBattery().then((battery) => {
  function updateAllBatteryInfo() {
    updateChargeInfo();
    updateLevelInfo();
    updateChargingInfo();
    updateDischargingInfo();
  }
  updateAllBatteryInfo();

  battery.addEventListener("chargingchange", () => {
    updateChargeInfo();
  });
  function updateChargeInfo() {
    console.log(`Battery charging? ${battery.charging ? "Yes" : "No"}`);
  }

  battery.addEventListener("levelchange", () => {
    updateLevelInfo();
  });
  function updateLevelInfo() {
    console.log(`Battery level: ${battery.level * 100}%`);
  }

  battery.addEventListener("chargingtimechange", () => {
    updateChargingInfo();
  });
  function updateChargingInfo() {
    console.log(`Battery charging time: ${battery.chargingTime} seconds`);
  }

  battery.addEventListener("dischargingtimechange", () => {
    updateDischargingInfo();
  });
  function updateDischargingInfo() {
    console.log(`Battery discharging time: ${battery.dischargingTime} seconds`);
  }
});
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

<!--
素で書くとMDNのサンプルコードはこんな感じです。
各イベントに対してaddEventListenerを使用しないといけなく、また、アンマウント時が考慮されていない形になります。VueUseはここをfor of文で一気にuseEventListenerします。
-->

---
layout: common-page
---

# VueUseで扱う利点とまとめ

- 値がリアクティブでUIの更新がしやすい
- 内部的にVueUseのuseEventListenerを使っているのでアンマウント時にListenerを解除
- 各イベントへのEventListenerの登録をしなくてよい

Chromiumでしか使えないのは難点ですが、バッテリーレベルに応じてダークモードにするなどに使っていけるかもしれません

<style>
  p {
    font-size: 1.6rem;
    font-weight: 400;
  }
</style>

<!--
VueUseで扱う利点とまとめはこのようになります。
値がリアクティブなこと、useEventListenerで各イベントに一気に登録するので楽なのと、アンマウントを気にしなくていいところでしょうか。

Chromiumでしか使えないのは難点ですが、バッテリーレベルに応じてダークモードにするなどに使っていけるかもしれません
-->

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

<!--
次はuseAnimateです
こちらはv10.0で追加された関数です
-->

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
</table>

<style>
  p {
    font-size: 1.8rem;
    margin-top: 1rem;
  }
</style>

<!--
useAnimateはWeb Animations APIを扱うものです。Web Animations APIは、CSSアニメーションのようなキーフレームに加え、再生、停止などを行うことができます。
-->

---
layout: common-page-code
---

# 使い方

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

<!--
使い方としてはこのような感じです。
こちらの返り値は、isSupported以外は、すべて通常のWeb Animation APIで得られるものと同様になっています。
-->

---
---

<UseAnimate />

<!--
こちらのデモはこのようになっています。
これはCSSのfilterで暗くした奥の絵と、靴だけを切り抜いたpng画像を重ねています。
こちらのボタンで並んでいるように、再生、stop、逆再生などが行なえます。再生中の状態によって、stateが変わるのがご覧いただけると思います。
-->

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

<!--
こちらのコードです。
こちらは完全に、useAnimateの呼び出しのみを行っています。すごくシンプルですね。少しゆっくりスクロールします。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
export function useAnimate(
  target: MaybeComputedElementRef,
  keyframes: UseAnimateKeyframes,
  options?: number | UseAnimateOptions,
): UseAnimateReturn {
  let config: UseAnimateOptions
  let animateOptions: undefined | number | KeyframeAnimationOptions

  if (isObject(options)) {
    config = options
    animateOptions = objectOmit(options, ['window', 'immediate', 'commitStyles', 'persist', 'onReady', 'onError'])
  }
  else {
    config = { duration: options }
    animateOptions = options
  }
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

<!--
VueUse本体のコードです。素のWeb Animation APIでも、オプション引数がオブジェクトでなく数値だった場合、durationとなるので、そちらが処理されているのがわかります。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
...
// requestAnimationFrameごとに関数を呼び出す。一時停止と再開のコントロール付き
const { resume: resumeRef, pause: pauseRef } = useRafFn(() => {
    if (!animate.value) return
    store.pending = animate.value.pending
    store.playState = animate.value.playState
    store.replaceState = animate.value.replaceState
    store.startTime = animate.value.startTime
    store.currentTime = animate.value.currentTime
    store.timeline = animate.value.timeline
    store.playbackRate = animate.value.playbackRate
  }, { immediate: false })

function syncResume() {
    if (isSupported.value)
      resumeRef()
  }

function syncPause() {
  if (isSupported.value && window)
    window.requestAnimationFrame(pauseRef)
}
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

<!--
useAnimateの中ではuseRafFnというのを使っています。こちらはrequestAnimationFrameごとに関数を呼び出すもので、返り値で一時停止と再開のコントロールを受け取ります。
syncResumeはアニメーションを継続し、syncPauseはpauseRefの中でcancelAnimationFrameします。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
...
  const play = () => {
    if (animate.value) {
      try {
        animate.value.play()
        syncResume()
      }
      catch (e) {
        syncPause()
        onError(e)
      }
    }
    else {
      update()
    }
  }
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

<!--
その関数たちを、実際に返り値として渡すplay関数などで処理するようになっています。pauseやcancelなどもこれと大体同様のコードになっています。
-->

---
layout: common-page-code
---

# VueUse本体のコード

```ts
...
// 安全なonMounted。コンポーネントのライフサイクルの中にある場合はonMounted()を呼び出します
tryOnMounted(() => {
  nextTick(() => update(true))
})

// 安全な onScopeDispose。エフェクト・スコープのライフサイクルの中にあればonScopeDispose()を呼び出す。
tryOnScopeDispose(cancel)
...
```

<!--
ここでもtryOnMountedとtryOnScopeDisposeが使われています。本当にVueUseはマウントとアンマウントを気にかけてくれているのがわかりますね。
-->

---
layout: common-page-code
---

# 素で書こうとするとこんな感じ

```ts
const nommingCake = document
  .getElementById("eat-me_sprite")
  .animate(
    [{ transform: "translateY(0)" }, { transform: "translateY(-80%)" }],
    {
      fill: "forwards",
      easing: "steps(4, end)",
      duration: aliceChange.effect.getComputedTiming().duration / 2,
    }
  );

nommingCake.pause();
nommingCake.playbackRate
```

<style>
  .slidev-code {
    height: 60vh !important;
  }
</style>

<!--
素で書こうとするとこのような感じです。毎回オブジェクトからメソッドやプロパティの呼び出しを行うので、これがコンポーザブル関数の返り値としてそれぞれ返ってくるならすごくシンプルですね。
-->

---
layout: common-page
---

# VueUseで扱う利点とまとめ

- 値がリアクティブでUIの更新がしやすい
- isSupported
- マウント時に再設定、アンマウント時にキャンセルを行う

コンポーザブル関数の呼び出しだけでstateと制御メソッドが得られるので便利

<style>
  p {
    font-size: 1.6rem;
    font-weight: 400;
  }
</style>

<!--
VueUseで扱う利点とまとめです。
値がリアクティブでUIの更新がしやすいのはもちろん、関数呼び出しのみで色々な値がシンプルに受け取れるのはいいと思います。
-->

---
layout: common-page
---

# 他にも関数はたくさん！

- Web API関連の他にも、Event関連や様々なAdd-onがあります🤗
  - ゲーム作るなら
    - @vueuse/gesture, @vueuse/sound, useDeviceMotion, useFullscreen ...etc
  - UI作るなら
    - useDraggable, useInfiniteScroll

...etc

<!--
他にも関数はたくさんあります！
ゲーム作るなら@vueuse/gesture, @vueuse/soundあたりがすごく使えるのかなと思っています。
UI作るなら、でいうと挙げきれないのですが、useDraggable, useInfiniteScrollあたりは便利だと思っています。
-->

---
layout: common-page
---

# まとめ

- VueUseの関数はアイデアの宝庫
- VueUseを使ったことがない方にもちょっとでも興味をもってもらえると嬉しい
- マウント時とアンマウント時を本当に気にしてくれてる
- VueUseはコンポーザブル関数の集まりなので、関数1ファイルで結構把握出来るのでコードを読んだり、自作のコンポーザブル関数の参考にするなどおすすめ
  - ただ、現在新しい関数の受け付けはスローダウンしているようなので、コントリビューションは気をつけよう

<!--
まとめです
VueUseの関数はアイデアを与えてくれます。
VueUseを使ったこと無い方にもちょっとでも興味持ってもらえたら嬉しいと思います！
VueUseはコンポーザブル関数の集まりなので、ちょっとコードを読むのもやりやすいですし、自作のコンポーザブル関数の参考にするのもおすすめです。ただし、現在新しい関数の受付はスローダウンしているようなので、コントリビューションする時は気をつけましょう。
-->

---
layout: end
---

<!--
終わりです、ご清聴ありがとうございました！
-->
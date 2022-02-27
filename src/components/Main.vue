<template>
  <div class="main">
    <div class="contents">
      <div class="works-sec">
        <div class="works-title-wrap">
          <h2 class="works-title bubble">WORKS</h2>
        </div>
        <div class="works-wrap">
          <div class="work-wrap">
            <img class="work-img" src="@/assets/memorandum.png" alt="" />
            <h3 class="work-title">くらげのダースが書くプログラミング備忘録</h3>
            <div class="work-exp">
              <p>「自分のわからなかったところを残せる」</p>
              <p>「文章にすることで理解を深められる」</p>
              <p>「色々な技術を試しながらサイト作りの経験ができる」</p>
              <p>等の理由から、このような備忘録サイトを作りました。</p>
              <p>今のところの機能としては、自分だけが投稿するという形で作っています。</p>
              <p>また、このサイトは主にvueを使っており、firebaseに保存をしています。</p>
              <p>コードが見たい方は、私のgithubアカウントから閲覧ください。</p>
            </div>
          </div>
          <div class="work-wrap">
            <img class="work-img" src="@/assets/MakeInfluencer.png" alt="" />
            <h3 class="work-title">MakeInfluencer</h3>
            p
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({});
</script>

<style lang="sass" scoped>
$base-color: #99CCFF

.contents
  opacity: 0.75
  background-color: $base-color

.bubble
  background: radial-gradient($base-color 50%, white 100%)
  border-radius: 50%
  text-align: center

.works-sec
  display: flex
  height: 200vh

.works-title-wrap
  flex: 2
  height: 100vh
  position: sticky
  top: 0

.works-title
  position: absolute
  border-radius: 50%
  top: 50%
  left: 50%
  transform: translate(-50%,-50%)
  font-size: 7rem
  width: 30rem
  line-height: 30rem
  text-align: center
  color: white

.works-wrap
  height: 200vh
  flex: 3
  background-color: white
  text-align: center

.work-wrap
  height: 100vh

.work-img
  margin: 5rem auto
  width: 40rem
  position: sticky
  top: 5rem

.work-title
  font-size: 2rem

.work-exp
  margin: 3rem
  p
    font-size: 1.3rem
    margin-top: 0.8rem
</style>

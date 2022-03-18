<template>
  <div class="works">
    <div class="contents">
      <h2 class="works-title">WORKS</h2>
      <div class="works-wrap">
        <div class="work-wrap1">
          <div class="work-flex1">
            <div class="work-important1">
              <img class="work-img" src="@/assets/memorandum.png" alt="" />
              <h3 class="work-title">くらげのダースが書くプログラミング備忘録</h3>
            </div>
          </div>
          <div class="work-flex2">
            <div class="work-exp">
              <p>制作日: 2022/01</p>
              <p>主な使用技術: vue.js firebase</p>
              <p>機能: ページ投稿機能(これは今のところ私のみが使える機能) ログイン機能 コメント機能</p>
              <p>
                目的:
                独学時代にこれの元となるサイトを作っていました。vueを学んだ後、そのサイトを大きく改良できると思い、vueを使って改良を始めました。元々は、「自分のわからなかったところを残せる」
                「文章にすることで理解を深められる」 「自分と同じ初心者の役に立ちたい」 等の理由から、このような備忘録サイトを作りました。
              </p>
              <p>
                概要:
                記事を投稿したいと思ったときは、まずvscodeでこのプロダクトのディレクトリに入っているviewsディレクトリに記事を書きます。そしてrouterでその記事にURLを生成し、サイトの投稿画面にタイトルやそのURL等を打ち込みます。すると自動的にサイトにそのページ欄を生成することができます。また、種類がWORKSなのかMEMORANDUMなのかを投稿時に指定し、それぞれの種類のみのページを表示することもできます。
              </p>
              <p>
                URL:
                <a href="https://pageofdarse.web.app/">https://pageofdarse.web.app/</a>
                <br />
                (元となったサイト→
                <a href="https://darse73.github.io/PageOfDarse-before/TOP/">https://darse73.github.io/PageOfDarse-before/TOP/</a>
                )
              </p>
              <p>
                github:
                <a href="https://github.com/darse73/PageOfDarse-before">https://github.com/darse73/PageOfDarse-before</a>
              </p>
            </div>
          </div>
        </div>
        <div class="work-wrap2">
          <div class="work-flex1">
            <div class="work-important2">
              <img class="work-img" src="@/assets/MakeInfluencer.png" alt="" />
              <h3 class="work-title">MakeInfluencer</h3>
            </div>
          </div>
          <div class="work-flex2">
            <div class="work-exp">
              <p>制作日: 2021/12</p>
              <p>主な使用技術: vue.js firebase スナップショット検索API YouTubeDataAPI</p>
              <p>機能: お勧め動画投稿機能 youtube、ニコニコ動画の埋もれている動画紹介</p>
              <p>目的: コロナの影響で増えている自宅時間を、少しでも豊かにしたいという思いから作りました。</p>
              <p>
                概要:
                初めてのチーム開発で作ったプロダクトです。チーム人数は４人で、制作期間は１か月です。役割分担によるスピード感や、アイデアの出の多さなど、チーム開発の良さを体感できました。
                また、複数人だからこそ起こるコンフリクトや意見の共有などの難しさも体感できました。チームで作ったものを完成させたときに仲間と分かち合った喜びはとてもよかったです。
              </p>
              <p>
                URL:
                <a href="https://pageofdarse.web.app/">https://pageofdarse.web.app/</a>
              </p>
              <p>
                github:
                <a href="https://github.com/darse73/PageOfDarse-before">https://github.com/darse73/PageOfDarse-before</a>
              </p>
            </div>
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
$base-color: #6ab5ff

.works
  color: white

.contents
  opacity: 0.75
  background-color: $base-color
  padding: 3rem 10%

.works-title
  margin: 0 auto
  border-radius: 50%
  font-size: 3rem
  width: 15rem
  line-height: 15rem
  position: sticky
  top: 3rem
  z-index: 100
  opacity: 0.8
  // 泡の形
  background: radial-gradient($base-color 50%, white 100%)
  border-radius: 50%
  text-align: center

.work-wrap1
  display: flex
  padding: 12rem 0

.work-flex1
  flex: 1

@mixin work-important($top, $padding)
  top: $top
  padding: $padding
  text-align: center
  position: sticky

.work-important1
  @include work-important(15rem, 15rem 10%)

.work-important2
  @include work-important(25rem, 8rem 3rem)

.work-img
  margin: 0rem auto 3rem
  width: 100%

.work-title
  font-size: 2.1rem

.work-wrap2
  display: flex
  padding-top: 12rem

.work-flex2
  flex: 1
  overflow: hidden
  position: sticky
  top: 12rem

.work-exp
  padding: 0 10%
p
  margin-bottom: 2rem
a
  font-size: 1.8rem
</style>
<template>
  <div class="about">
    <Wave2 />
    <div class="contents">
      <h2 class="about-title">ABOUT</h2>
      <div class="img-and-basic">
        <div class="about-flex1">
          <div class="soccer-wrap">
            <img src="@/assets/soccer.jpg" alt="" class="soccer" />
          </div>
        </div>
        <div class="about-flex2">
          <div class="basic-info">
            <ul>
              <li>福岡大学・理学部・物理科学科 ３年</li>
              <li>兒玉侑也</li>
            </ul>
          </div>
        </div>
      </div>
      <div class="hobby">
        <h3 class="hobby-title">HOBBY</h3>
        <ul>
          <div class="prev" @click="prev"></div>
          <li :ref="imageRef" v-for="image in images" :key="image.id">
            <img :src="image.src" />
          </li>
          <div class="next" @click="next"></div>
        </ul>
        <ul class="hobby-comment">
          <li :ref="commentRef" class="comment-1">
            <p>
              ドラムは小学１年生から６年生の時まで習っており、大学生になってまた時間があるときに叩くことが増えました。自分がたたけなかったフレーズが一つずつ叩けるようになり、一曲を通して叩けるようになると達成感を感じられます。また、曲に合わせて叩くのが楽しく、もっと上達し色々な曲を叩けるように練習していきます。
            </p>
          </li>
          <li :ref="commentRef" class="comment-2">
            <p>プログラミングを始めたのは大学3年生の夏からです。</p>
            <p>最初は独学で始め、10月からは３か月プログラミングコミュニティのチーム開発コースに参加しました。</p>
            <p>今でも勉強意欲は高まっており、毎日試行錯誤しながらサイトを作っています。</p>
          </li>
          <li :ref="commentRef" class="comment-3">
            <p>サッカーは小学５年生から高校３年生までやっており、父が元々サッカーをしていたのが始めたきっかけです。</p>
            <p>
              正直私は小さいころ泣き虫だったのですが、サッカーを始めたおかげで心身ともに強くなることができ、たくさんのいい仲間と出会えたと感じています。
            </p>
            <p>今はコロナ禍で友達と集まってするということができていないのですが、コロナが終わったらまたしたいです。</p>
          </li>
        </ul>
      </div>
      <div class="studying">
        <h3 class="studying-title">STUDYING</h3>
        <div class="studying-list">
          <img src="@/assets/html-5.svg" alt="" />
          <img src="@/assets/css-3.svg" alt="" />
          <img src="@/assets/sass.svg" alt="" />
          <img src="@/assets/javascript.svg" alt="" />
          <img src="@/assets/typescript-icon.svg" alt="" />
          <img src="@/assets/vue.svg" alt="" />
          <img src="@/assets/github-icon.svg" alt="" />
          <img src="@/assets/git.svg" alt="" />
          <img src="@/assets/firebase.svg" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from "vue";
import Wave2 from "@/components/Wave2.vue";

export default defineComponent({
  components: {
    Wave2,
  },
  setup() {
    const images = reactive({
      dram: {
        src: require("@/assets/dram.jpg"),
        id: 0,
      },
      programming: {
        src: require("@/assets/programming.jpg"),
        id: 1,
      },
      soccer: {
        src: require("@/assets/soccer2.jpg"),
        id: 2,
      },
    });

    const imageRefs = ref<HTMLImageElement[]>([]);

    const imageRef = (el: any) => {
      if (el) {
        imageRefs.value.push(el);
      }
    };

    const commentRefs = ref<HTMLLIElement[]>([]);

    const commentRef = (el: any) => {
      if (el) {
        commentRefs.value.push(el);
      }
    };

    let curDeg = 0;

    const prev = () => {
      for (let i = 0; i < imageRefs.value.length; i++) {
        const imgElem = imageRefs.value[i];
        const commElem = commentRefs.value[i];
        let deg = curDeg + 120 * i - 120;
        imgElem.style.transform = `rotateY(${deg}deg) translateZ(250px)`;
        commElem.style.transform = `rotateY(${deg}deg) translateZ(250px)`;
        if (deg % 360 === 0) {
          commElem.style.opacity = "1";
        } else {
          commElem.style.opacity = "0.1";
        }
        console.log(commentRefs.value);
      }

      curDeg -= 120;
    };

    const next = () => {
      for (let i = 0; i < imageRefs.value.length; i++) {
        const imgElem = imageRefs.value[i];
        const commElem = commentRefs.value[i];
        let deg = curDeg + 120 * i + 120;
        imgElem.style.transform = `rotateY(${deg}deg) translateZ(250px)`;
        commElem.style.transform = `rotateY(${deg}deg) translateZ(250px)`;
        if (deg % 360 === 0) {
          commElem.style.opacity = "1";
        } else {
          commElem.style.opacity = "0.1";
        }
        console.log(commentRefs.value);
      }
      curDeg += 120;
    };

    return {
      images,
      prev,
      next,
      imageRef,
      commentRef,
    };
  },
});
</script>

<style lang="sass" scoped>
$base-color: #6ab5ff

.contents
  opacity: 0.75
  padding: 5rem

.about-title
  color: $base-color
  margin: 0 auto 5rem
  border-radius: 50%
  font-size: 3rem
  width: 15rem
  line-height: 15rem
  position: sticky
  top: 3rem
  z-index: 100
  opacity: 0.8
  background: radial-gradient(white 50%, $base-color 70%)
  text-align: center

.img-and-basic
  display: flex
  margin-bottom: 15rem

.about-flex1
  flex: 1

.soccer-wrap
  padding: 12rem 10%
  text-align: center

.soccer
  width: 70%

.about-flex2
  flex: 1

.basic-info
  padding: 12rem 10%

  ul
    text-align: center

    li
      &:first-child
        font-size: 2rem
        margin: 7rem 0 5rem

      &:last-child
        text-align: center
        font-size: 5rem

.hobby
  padding-bottom: 30rem

  .hobby-title
    text-align: center
    font-size: 2.5rem
    margin-bottom: 3rem
  ul
    position: relative
    width: 250px
    transform-style: preserve-3d
    perspective: 10000px
    height: 18.71rem
    margin: 0 auto

    @mixin allow
      border-top: 1rem solid transparent
      border-bottom: 1rem solid transparent
      height: 0
      position: absolute
      top: 50%
      transform: translateY(-50%)
      filter: drop-shadow(0px 3px 0px $base-color)
      cursor: pointer
    .prev
      @include allow
      border-right: 1rem solid black
      left: -25rem
    .next
      @include allow
      border-left: 1rem solid black
      right: -25rem

    @mixin hobby-child($transform)
      position: absolute
      width: 250px
      transform: $transform
      transition: transform 3s
      img
        width: 100%

    li
      &:first-of-type
        @include hobby-child(rotateY(0deg) translateZ(25rem))
      &:nth-of-type(2)
        @include hobby-child(rotateY(120deg) translateZ(25rem))
      &:last-of-type
        @include hobby-child(rotateY(240deg) translateZ(25rem))

  .hobby-comment
    position: relative
    width: 50%
    margin: 0 auto
    transform-style: preserve-3d
    perspective: 10000px

    @mixin comment ($transform, $opacity)
      width: 100%
      margin: 5rem auto
      position: absolute
      transform: $transform
      opacity: $opacity
      transition: all 3s
    li
      &:first-of-type
        @include comment(rotateY(0deg) translateZ(25rem), 1)
      &:nth-of-type(2)
        @include comment(rotateY(120deg) translateZ(25rem), 0.1)
      &:last-of-type
        @include comment(rotateY(240deg) translateZ(25rem), 0.1)

.studying
  .studying-title
    text-align: center
    font-size: 2.5rem
    margin-bottom: 3rem
  .studying-list
    display: grid
    justify-items: center
    align-items: center
    grid-template-columns: repeat(3, 1fr)
    grid-template-rows: repeat(3, 1fr)
    padding: 0 20% 1rem
    img
      width: 30%
</style>

<template>
  <div ref="headerRef" class="header">
    <div class="title">
      <h1 ref="titleT" class="title-t">DARSE</h1>
      <h1 ref="titleB" class="title-b">Portfolio Of Kodama Yuya</h1>
    </div>
    <div ref="slideRef" class="slide"><img :src="slideImg" alt="" class="slide-img" /></div>
    <Wave class="wave" />
    <div class="ship-field">
      <div class="ship-container">
        <img ref="smokeRef" src="@/assets/smoke.png" alt="" class="steam1" />
        <img src="@/assets/smoke.png" alt="" class="steam2" />
        <img src="@/assets/smoke.png" alt="" class="steam3" />
        <img src="@/assets/ship.png" alt="" class="ship" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed, onMounted, watch } from "vue";
import Wave from "@/components/Wave.vue";

export default defineComponent({
  components: {
    Wave,
  },
  setup() {
    const slideImgs = ref([
      require("@/assets/soccer.jpg"),
      require("@/assets/memorandum.png"),
      require("@/assets/MakeInfluencer.png"),
      require("@/assets/dram.jpg"),
      require("@/assets/programming.jpg"),
      require("@/assets/soccer2.jpg"),
    ]);

    const titleT = ref<HTMLHeadingElement>();
    const headerRef = ref<HTMLDivElement>();
    const smokeRef = ref<HTMLImageElement>();
    const slideRef = ref<HTMLDivElement>();
    const slideImg = ref(slideImgs.value[0]);
    let i = ref(1);

    onMounted(() => {
      const smokePosition = ref();
      const smokeLeft = ref();
      let smokeWidth = 0;
      const smokeCenter = ref();
      const slidePosition = ref();
      const slideRight = ref();
      const slideLeft = ref();
      let slideWidth = 0;
      const slideCenter = ref();

      smokePosition.value = smokeRef.value?.getBoundingClientRect();
      smokeLeft.value = smokePosition.value?.left || 0;
      smokeWidth = smokePosition.value.width || 0;
      smokeCenter.value = smokeLeft.value + smokeWidth / 2;

      slidePosition.value = slideRef.value?.getBoundingClientRect();
      slideRight.value = slidePosition.value?.right || 0;
      slideLeft.value = slidePosition.value?.left || 0;
      slideWidth = slidePosition.value.width || 0;
      slideCenter.value = slideLeft.value + slideWidth / 2;

      const test = () => {
        smokePosition.value = smokeRef.value?.getBoundingClientRect();
        smokeLeft.value = smokePosition.value?.left || 0;
        smokeCenter.value = smokeLeft.value + smokeWidth / 2;
      };
      setInterval(test, 1);

      const resize = () => {
        slidePosition.value = slideRef.value?.getBoundingClientRect();
        slideRight.value = slidePosition.value?.right || 0;
        slideLeft.value = slidePosition.value?.left || 0;
        slideCenter.value = slideLeft.value + slideWidth / 2;
        console.log(slideRight.value);
        console.log(slideLeft.value);
        headerWidth = headerRef.value?.clientWidth || 0;
        slideDur = slideWidth / ((headerWidth - 350) / 12.5);
      };
      window.addEventListener("resize", resize);

      let headerWidth = headerRef.value?.clientWidth || 0;
      let slideDur = slideWidth / ((headerWidth - 350) / 12.5);
      console.log(slideDur);
      let slideLock = "lock";
      watch(smokeCenter, () => {
        if (smokeCenter.value <= slideRight.value) {
          if (smokeCenter.value >= slideRight.value - 10) {
            slideRef.value?.style.setProperty("--ani-dur", `${slideDur}s`);
            slideLock = "open";
          } else if (smokeCenter.value < slideLeft.value) {
            slideRef.value?.style.setProperty("--ani-dur", ``);
            slideLock = "lock";
          }
        }
        if (smokeCenter.value >= slideLeft.value) {
          if (smokeCenter.value <= slideLeft.value + 10) {
            slideRef.value?.style.setProperty("--ani-dur", `${slideDur}s`);
            slideLock = "open";
          } else if (smokeCenter.value > slideRight.value) {
            slideRef.value?.style.setProperty("--ani-dur", ``);
            slideLock = "lock";
          }
        }
        if (smokeCenter.value >= slideCenter.value - 0.5) {
          if (smokeCenter.value <= slideCenter.value + 0.5) {
            if (slideLock === "open") {
              console.log("d");
              slideImg.value = slideImgs.value[i.value];
              i.value++;
              if (i.value === 6) {
                i.value = 0;
              }
            }
          }
        }
      });
    });

    return {
      titleT,
      headerRef,
      slideRef,
      slideImg,
      smokeRef,
    };
  },
});
</script>

<style lang="sass" scoped>
@use "sass:math"

.header
  height: 100vh

  .title
    z-index: 10

    .title-t
      position: absolute
      top: 15%
      left: 10%
      font-size: 7.2rem
      letter-spacing: 0.8rem

    .title-b
      position: absolute
      top: 70%
      left: 60%
      font-size: 1.6rem
      margin-left: 6rem
      z-index: 1000

  .slide
    width: 40rem
    height: 25rem
    position: absolute
    top: 50%
    left: 50%
    transform: translate(-50%, -50%)
    transform-origin: center
    overflow: hidden
    animation: slide ease-in-out var(--ani-dur)

    @keyframes slide
      0%
        transform: translate(-50%, -50%) rotateX(0)
      100%
        transform: translate(-50%, -50%) rotateX(-3600deg)

    img
      position: absolute
      top: 50%
      left: 50%
      transform: translate(-50%, -50%)
      width: 100%

  .wave
    position: absolute
    bottom: 0
    z-index: 1

  .ship-field
    width: 100%
    height: 100%
    position: absolute
    bottom: 0rem
    overflow: hidden

    .ship-container
      width: 100%
      height: 100%
      position: relative
      animation: x-move linear 25s infinite

      @mixin steam
        width: 8rem
        position: absolute
        right: 6.3rem
        bottom: 30.2rem
        transform-origin: bottom
        transform: rotate(30deg)
        animation: steam infinite 3s backwards linear

      .steam1
        @include steam
        animation-delay: 0s

      .steam2
        @include steam
        animation-delay: 1s

      .steam3
        @include steam
        animation-delay: 2s

      @keyframes steam
        0%
          opacity: 0
          transform: scaleY(0)
        50%
          opacity: 1
          transform: scaleY(2.5)
        100%
          opacity: 0
          transform: scaleY(5)

      .ship
        width: 35rem
        position: absolute
        right: 0
        bottom: 11rem
        transform-origin: center
        animation: ship ease-in-out 1.7s infinite alternate
        z-index: -1

      @keyframes x-move
        0%
          transform: translateX(0)
        49%
          transform: translateX(calc(-100% + 35rem))
        50%
          transform: scale(-1, 1)
        99%
          transform: translateX(calc(100% - 35rem)) scale(-1, 1)
        100%
          transform: scale(1)

      @keyframes ship
        0%
          transform: translateY(1rem) rotate(6deg)
        100%
          transform: translateY(0) rotate(2deg)
</style>
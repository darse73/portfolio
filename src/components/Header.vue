<template>
  <div class="header">
    <div class="title-top">DARSE</div>
    <div class="title-bottom">Portfolio Of Kodama Yuya</div>
    <div class="slide"><img src="" alt="" class="slide-img" /></div>
    <Wave class="wave" />
    <div class="ship-field">
      <div class="ship-container">
        <img src="@/assets/smoke.png" alt="" class="steam1" />
        <img src="@/assets/smoke.png" alt="" class="steam2" />
        <img src="@/assets/smoke.png" alt="" class="steam3" />
        <img src="@/assets/ship.png" alt="" class="ship" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Wave from "@/components/Wave.vue";

export default defineComponent({
  components: {
    Wave,
  },
});
</script>


<style lang="sass" scoped>
@use "sass:math"

.header
  height: 100vh
  position: relative

@mixin title
  transform: rotate(-15deg)
  position: absolute

.title-top
  @include title
  top: 31%
  left: 14%
  font-size: 7.2rem
  letter-spacing: 0.8rem
.title-bottom
  @include title
  top: 47%
  left: 20%
  font-size: 1.6rem

.slide
  border: 0.1rem solid black
  width: 35rem
  height: 20rem
  position: absolute
  top: 17%
  left: 55%

  @mixin allow
    content: ""
    position: absolute
    top: 50%
    transform: translateY(-50%)
    border-top: 1rem solid transparent
    border-bottom: 1rem solid transparent

  &:before
    @include allow
    left: -5rem
    border-right: 1rem solid black
  &:after
    @include allow
    right: -5rem
    border-left: 1rem solid black

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
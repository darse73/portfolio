<template>
  <div class="main">
    <div class="flame-t"></div>
    <div class="flame-r"></div>
    <div class="flame-b"></div>
    <div class="flame-l"></div>
    <div class="flame-up-l"></div>
    <div class="flame-up-r"></div>
    <div class="flame-low-r"></div>
    <div class="flame-low-l"></div>
    <div class="contents">
      <div class="works-sec">
        <div class="works-title bubble">WORKS</div>
        <div class="work1 work bubble"><img src="" alt="" /></div>
        <div class="work2 work bubble"><img src="" alt="" /></div>
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

@mixin grid-child($column, $row, $bg)
  grid-column: $column
  grid-row: $row
  background: $bg
  opacity: 0.75

.main
  display: grid
  grid-template-columns: 20% 1fr 20%
  grid-template-rows: 20rem 100rem 20rem

.flame-t
  @include grid-child(2, 1, linear-gradient($base-color, lighten($base-color, 15%)))

.flame-r
  @include grid-child(3, 2, linear-gradient(to left, $base-color, lighten($base-color, 15%)))

.flame-b
  @include grid-child(2, 3, linear-gradient(to top, $base-color, lighten($base-color, 15%)))

.flame-l
  @include grid-child(1, 2, linear-gradient(to right, $base-color, lighten($base-color, 15%)))

.flame-up-l
  @include grid-child(1, 1, radial-gradient(at 100% 100%, lighten($base-color, 15%), $base-color 70%))

.flame-up-r
  @include grid-child(3, 1, radial-gradient(at 0% 100%, lighten($base-color, 15%), $base-color 70%))

.flame-low-r
  @include grid-child(3, 3, radial-gradient(at 0% 0%, lighten($base-color, 15%), $base-color 70%))

.flame-low-l
  @include grid-child(1, 3, radial-gradient(at 100% 0%, lighten($base-color, 15%), $base-color 70%))

.contents
  grid-column: 2
  grid-row: 2
  opacity: 0.75
  background-color: lighten($base-color, 15%)

.bubble
  background: radial-gradient(lighten($base-color, 15%) 50%, $base-color 100%)
  border-radius: 50%
  text-align: center

.works-sec
  position: relative

.works-title
  position: absolute
  left: 10%
  top: 15rem
  font-size: 5rem
  width: 30rem
  line-height: 30rem

.work
  position: absolute
  width: 25rem
  height: 25rem

.work1
  top: 30rem
  right: 10%

.work2
  top: 60rem
  left: 40%
</style>

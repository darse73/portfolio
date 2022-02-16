<template>
  <div class="header">
    <div class="title-top">DARSE</div>
    <div class="title-bottom">Portfolio Of Kodama Yuya</div>
    <div class="slide"><img src="" alt="" class="slide-img" /></div>
    <Wave />
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
  font-size: 4.5rem
  letter-spacing: 0.5rem
.title-bottom
  @include title
  top: 47%
  left: 18%

.slide
  border: 0.1rem solid black
  width: 30rem
  height: 17rem
  position: absolute
  top: 15%
  left: 50%

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
</style>

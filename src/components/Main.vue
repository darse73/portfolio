<template>
  <div class="main">
    <div class="works-sec">
      <div class="works-title bubble">WORKS</div>
      <div class="work1 work bubble"><img src="" alt="" /></div>
      <div class="work2 work bubble"><img src="" alt="" /></div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({});
</script>

<style lang="sass" scoped>
$base-color: #99CCFF
.main
  background: radial-gradient(blue, $base-color 70%)
  height: 200vh
  opacity: 0.75
  position: relative

.bubble
  background-color: white
  border-radius: 50%
  text-align: center

.works-title
  position: absolute
  left: 20%
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
  right: 20%

.work2
  top: 60rem
  left: 40%
</style>

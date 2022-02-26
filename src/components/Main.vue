<template>
  <div class="main">
    <div class="contents">
      <div class="works-sec">
        <div class="works-title-wrap">
          <div class="works-title bubble">WORKS</div>
        </div>
        <div class="work-wrap">
          <div class="work1-wrap">
            <div class="work1 work bubble"><img src="" alt="" /></div>
          </div>
          <div class="work2 work bubble"><img src="" alt="" /></div>
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
  background: radial-gradient(white 50%, $base-color 60%)
  border-radius: 50%
  text-align: center

.works-sec
  display: flex
  height: 200vh

.works-title-wrap
  flex: 1
  height: 100vh
  position: sticky
  top: 0

.works-title
  position: absolute
  top: 50%
  left: 50%
  transform: translate(-50%,-50%)
  font-size: 5rem
  width: 30rem
  line-height: 30rem

.work-wrap
  height: 200vh
  flex: 1

.work1-wrap
  height: 100vh

.work1
  margin:
    top: 30rem
    right: 10%

.work2
  margin:
    top: 60rem
    left: 40%
</style>

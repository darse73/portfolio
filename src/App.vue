<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default defineComponent({
  components: {
    Header,
    Main,
  },
});
</script>

<style lang="sass">
*
  margin: 0
  padding: 0
  font-weight: normal
  list-style: none

html
  font-size: 62.5%

p
  letter-spacing: 0.2rem
  font-size: 1.6rem
  line-height: 1.8em
</style>

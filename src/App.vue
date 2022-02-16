<template>
  <div id="app">
    <Header />
    <div class="div"></div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Header from "@/components/Header.vue";

export default defineComponent({
  components: {
    Header,
  },
});
</script>

<style lang="sass">
*
  margin: 0
  padding: 0
</style>

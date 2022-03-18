<template>
  <div class="main">
    <Works />
    <About />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Works from "@/components/Works.vue";
import About from "@/components/About.vue";

export default defineComponent({
  components: {
    Works,
    About,
  },
});
</script>


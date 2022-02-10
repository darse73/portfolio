<template>
<div id="app">
   <Header />
  <div class="div">
   </div>
  </div>

</template>

<script>
import { defineComponent } from '@vue/composition-api'
import Header from "@/components/Header.vue"

export default defineComponent({
  components: {
    Header
  },
  setup() {
    
  },
})
</script>


<style lang="stylus">
*
  margin: 0
  padding: 0
</style>

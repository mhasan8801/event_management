<template>
  <div id="app">
    <router-view/>
    <FooterComp />
  </div>
</template>

<script>
import FooterComp from "@/components/FooterComp.vue"

export default {
  components : {
    FooterComp
  }
}
</script>


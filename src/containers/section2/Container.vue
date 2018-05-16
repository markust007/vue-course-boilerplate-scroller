<template>
  <section id="section2">

    <Page1></Page1>

  </section>
</template>

<script>
import {elementInViewport} from '../../utils/viewport.js';
import Page1 from './pages/Page1.vue'

  export default {
    data: function () {
      return {

      }
    },
    computed: {
      location () {
        return this.$store.state.scormLMS.location
      }
    },
    methods: {

    },
    mounted() {

    },
    components: {
      Page1
    },
    props: []
  }
</script>

<style lang="scss" scoped>

</style>

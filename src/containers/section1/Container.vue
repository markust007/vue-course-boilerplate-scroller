<template>
  <section id="section1">

    <Page1 v-show="pageNum === 1" @pageUp="pageUp"></Page1>
    <Page2 v-show="pageNum === 2" @pageDown="pageDown"></Page2>

    <scroll @scroll="scroll('#section2')"></scroll>

  </section>
</template>

<script>
import scroll from '../../components/Scroll.vue'
import {sectionScroll} from '../../utils/scroll.js';
import Page1 from './pages/Page1.vue'
import Page2 from './pages/Page2.vue'

  export default {
    data() {
      return {
        pageNum: 1
      }
    },
    computed: {
      location () {
        return this.$store.state.scormLMS.location
      }
    },
    methods: {
      pageUp() {
        this.pageNum += 1
      },
      pageDown() {
        this.pageNum -= 1
      },
      scroll(section) {
        sectionScroll(section)
      }
    },
    mounted() {

    },
    components: {
      scroll, Page1, Page2
    },
    props: []
  }
</script>

<style lang="scss" scoped>

</style>

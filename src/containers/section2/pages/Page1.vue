<template>
  <div class="page1">
    <h3 v-html="items.s2page1[0].title" class="animated fadeInUp" v-show="anim.anim1"></h3>
    <p v-html="items.s2page1[0].text" class="animated fadeInUp" v-show="anim.anim2"></p>
  </div>
</template>

<script>
import {elementInViewport} from '../../../utils/viewport.js';

export default {
  data() {
    return {
      anim: {
        anim1: false,
        anim2: false,
      }
    };
  },

  computed: {
    location() {
      return this.$store.state.scormLMS.location
    },
    items() {
      return this.$store.state.items
    }
  },

  methods: {
    scroll() {
      let self = this
      let section2 = document.getElementById("section2")
      if (elementInViewport(section2)) {
        self.anim.anim1 = true
        setTimeout(() => {
          self.anim.anim2 = true
        }, 500);
      }
    },
    checkCue() {
      //BOILERPLATE FOR RUNNING AN INTERVAL
      // var self = this
      // if(Math.floor(self.$refs.audio1.currentTime) == 3){
      //   self.vis1 = "visible"
      // }
    },
    runInterval() {
      //BOILERPLATE FOR RUNNING AN INTERVAL
      this.interval = setInterval(this.checkCue, 100);
    }
  },
  mounted() {
    window.addEventListener('scroll', this.scroll)
  },
  beforeDestroy() {
    //BOILERPLATE FOR RUNNING AN INTERVAL
    clearInterval(this.interval);
  },
  components: {},
  props: []
};
</script>

<style lang="scss" scoped>

</style>

<template>
  <div id="app" v-if="items && config">
    <!-- JIRA - REMOVE FOR GOLD -->
    <Jira v-if="config.jira"></Jira>
    <Jira-position v-if="config.jira"></Jira-position>

    <!-- LOADING ICON -->
    <transition name="fade">
      <i class="fa fa-circle-o-notch fa-spin fa-3x fa-fw" v-show="loader"></i>
    </transition>

    <!-- MAIN -->
    <Top :items="items"></Top>
    <Resources :items="items" v-show="menu"></Resources>
    <Section1></Section1>
    <Section2></Section2>

  </div>
</template>

<script>
/////////////////////IMPORTS/////////////////////////
/////////////////////////////////////////////////////
import store from './store/index'
import Jira from './components/Jira.vue'
import JiraPosition from './components/JiraPosition.vue'
import Top from './components/Top.vue'
import Resources from './components/Resources.vue'
import Section1 from './containers/section1/Container.vue'
import Section2 from './containers/section2/Container.vue'

import {polyfill} from "mobile-drag-drop";
import {scrollBehaviourDragImageTranslateOverride} from "mobile-drag-drop/scroll-behaviour";
/////////////////////VARIABLES & MISC/////////////////////
/////////////////////////////////////////////////////////
polyfill({
    // use this to make use of the scroll behaviour
    dragImageTranslateOverride: scrollBehaviourDragImageTranslateOverride
});

export default {
  name: 'app',
  store,
  data () {
    return {
      loader: true
    }
  },
  computed: {
    stateLocation () {
      return this.$store.state.scormLMS.location
    },
    menu () {
      return this.$store.state.menu.menu
    },
    items() {
      return this.$store.state.items
    },
    config() {
      return this.$store.state.config
    }
  },
  methods: {
    menuToggle () {
      this.$store.commit('menu/menuToggle')
    }
  },
  mounted() {
    this.loader = false;
    //scorm
    this.$store.commit('scormLMS/scormInit');
  },
  components: {
    Jira, JiraPosition, Top, Resources, Section1, Section2
  }
}
</script>

<!-- REMOVE 'SCOPED' FOR GLOBAL STYLES -->
<style lang="scss">

</style>

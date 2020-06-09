<template>
  <li
    :class="mapcontent.placeEn"
    v-if="checkDisplay"
  >
    <span>{{ mapcontent.placeCh }}</span>
    <article>
      <h4 @click="toggle">{{ mapcontent.title }}</h4>
      <SlideUpDown :active="active" v-html="mapcontent.article" />
    </article>
  </li>
</template>

<script>
import SlideUpDown from 'vue-slide-up-down'

export default {
  components: {
    SlideUpDown
  },
  props: {
    mapcontent: {
      type: Object,
      required: true
    },
    windowWidth: {
      type: Number,
      default: null
    },
    activeList: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      active: null
    }
  },
  watch: { 
    windowWidth: function() {
      this.active = this.windowWidth >= 1024 ? false : true
    }
  },
  methods: {
    toggle() {
      if(this.windowWidth >= 1024) this.active = !this.active
    }
  },
  computed: {
    checkDisplay() {
      if(this.windowWidth < 1024) {
        return this.mapcontent.placeEn === this.activeList ? true : false
      }
      return true
    }
  }
}
</script>


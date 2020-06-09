<template>
  <transition name="fade">
    <li
      :class="mapcontent.placeEn"
      v-if="checkDisplay"
    >
      <img
        v-if="!showMap"
        :src="mapcontent.image"
        :alt="mapcontent.placeCh"
        data-aos="fade"
      />
      <span>{{ mapcontent.placeCh }}</span>
      <article>
        <h4>{{ mapcontent.title }}</h4>
        <div v-html="mapcontent.article" />
      </article>
    </li>
  </transition>
</template>

<script>
export default {
  props: {
    mapcontent: {
      type: Object,
      required: true
    },
    activeList: {
      type: String,
      required: true
    },
    showMap: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    checkDisplay() {
      if(this.showMap) {
        return this.mapcontent.placeEn === this.activeList ? true : false
      }
      return true
    }
  }
}
</script>

<style>
.fade-enter-active {
  transform: translate(0, 0);
  opacity: 1;
  transition: .5s;
}
.fade-enter {
  transform: translate(10%, 0);
  opacity: 0;
}
.fade-leave-active,
.fade-leave-to
{
  display: none;
}
</style>
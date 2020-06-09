<template>
  <div :id="id" :class="isMobile ? 'mobile' : 'desktop'" />
</template>

<script>
export default {
  props: {
    size: Array,
    path: String,
    id: String,
    isMobile: Boolean
  },
  beforeCreate() {
    window.googletag.cmd.push(() => {
      window.googletag.destroySlots();
    });
  },
  mounted() {
    const { path, size, id } = this;
    window.googletag.cmd.push(() => {
      window.googletag.defineSlot(path, size, id).addService(window.googletag.pubads());
      window.googletag.pubads().enableSingleRequest();
      window.googletag.enableServices();
      window.googletag.display(id);
    });
  }
}
</script>

<style>
.wrapper.ad {
  width: 100%;
}
.mobile {
  width: 300px;
  margin: 6em auto;
}
.desktop {
  width: 970px;
  margin: 6em auto;
}

@media screen and (min-width: 1024px) {
  .mobile {
    display: none;
  }
}

@media screen and (max-width: 1023px) {
  .desktop {
    display: none;
  }
}

@media screen and (max-width: 480px) {
  .mobile {
    margin: 4em auto;
  }
}
</style>

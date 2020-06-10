<template>
  <div
    class="figuremask"
    @mousemove="getMouseX"
    @touchmove="touchmove"
    :style="{maxHeight: setMaxHeight + 'px'}"
  >
    <div class="figurebox" ref="area">
      <picture>
        <source srcset="../assets/images/urban_renewal_after.jpg" media="(min-width: 481px)">
        <source srcset="../assets/images/urban_renewal_after_m.jpg" media="(max-width: 480px)">
        <img src="../assets/images/urban_renewal_after.jpg" alt="" />
      </picture>
    </div>
    <div
      class="maskbox"
      :style="{
        width: this.mouseX + 'px',
        backgroundSize: boxWidth + 'px'
      }"
    />
    <i
      class="fa fa-sort centericon"
      :style="{left: this.mouseX + 'px'}"
      @mousemove.stop="getMouseX"
    />
    <ul v-if="element" v-html="element" @mousemove.stop="getMouseX" />
    <transition name="load">
      <div class="loadingMask" v-if="loading">
        <img src="../assets/images/loading.svg" alt="loading..." />
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      boxWidth: null,
      mouseX: null,
      areaOffset: null,
      appendIndex: 1,
      element: '',
      loading: true
    }
  },
  props: {
    isMobile: {
      type: Boolean,
      requiredtrue: true
    },
    windowWidth: {
      type: Number,
      requiredtrue: true
    }
  },
  watch: {
    windowWidth: function() {
      this.boxWidth = this.$refs.area.clientWidth;
      this.areaOffset = this.$refs.area.getBoundingClientRect().left;
      this.mouseX = this.boxWidth / 2;
    }
  },
  computed: {
    setMaxHeight() {
      const clientHeight = document.documentElement.clientHeight;
      return this.windowWidth > 480 ? clientHeight - 196 : clientHeight - 186;
    }
  },
  methods: {
    getMouseX(event) {
      if(!this.isMobile && !this.loading) {
        this.mouseX = event.clientX - this.areaOffset;
      }
    },
    touchmove(event) {
      if(this.isMobile && !this.loading) {
        const clientX = event.targetTouches[0].clientX - this.areaOffset;
        if(clientX > 0 && clientX < this.boxWidth) this.mouseX = clientX;
      }
    },
    runAnimate() {
      this.loading = false;
      const addElement = setInterval(() => {
        if(this.appendIndex > 7) {
          clearInterval(addElement);
        } else {
          this.element = this.element === '' ? 
            '<li><img src="images/maintext1.png" class="animate" /></li>' : 
            this.element.replace(/animate/g, '') + `<li><img src="images/maintext${this.appendIndex}.png" class="animate" /></li>`;
          this.appendIndex++;
        }
      }, 500)
    }
  },
  mounted() {
    window.addEventListener('load', this.runAnimate)
  },
  beforeDestroy() {
    window.removeEventListener('load', this.runAnimate);
  }
}
</script>

<style>
.figuremask {
  position: relative;
  cursor: e-resize;
  overflow: hidden;
}
.figuremask:before,
.figuremask:after {
  position: absolute;
  background: rgba(200, 61, 0, .75);
  color: white;
  font-weight: bold;
  top: 10%;
  padding: 0.2em 0.6em;
  z-index: 1;
}
.figuremask:before {
  content: 'Before';
  left: 0;
}
.figuremask:after {
  content: 'After';
  right: 0;
}
.figuremask img {
  display: block;
}
.figuremask .figurebox {
  overflow: hidden;
}
.figuremask .maskbox {
  position: absolute;
  overflow: hidden;
  width: 50%;
  height: 100%;
  left: 0;
  top: 0;
  border-right: solid 2px white;
  box-sizing: content-box;
  background-image: url('../assets/images/urban_renewal_before.jpg');
}
.figuremask .maskbox:before {
  content: '';
  position: absolute;
  width: 2px;
  height: 100%;
  background: white;
  top: 0;
  right: 0;
}
.figuremask .centericon {
  position: absolute;
  width: 50px;
  height: 50px;
  font-size: 30px;
  background: rgba(0, 0, 0, .5);
  border: solid 3px white;
  top: 50%;
  left: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  transform: translate(-50%, -50%) rotate(90deg);
}
.figuremask .centericon:before {
  color: white;
  background: rgba(0, 0, 0, .6);
}
.figuremask ul {
  position: absolute;
  top: 25%;
  width: 100%;
}
.figuremask ul li {
  width: 11%;
  display: inline-block;
  margin: 0 0.75%;
}
.figuremask ul li:nth-child(5) {
  margin-left: 2%;
}
.figuremask ul li img {
  display: block;
  width: 100%;
}
.figuremask ul li img.animate {
  animation-duration: .5s;
  animation-fill-mode: both;
  animation-name: slideInDown;
}
.loadingMask {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, .7);
}
.loadingMask img {
  width: 60px;
  -webkit-animation-name: rotate;
  animation-name: rotate;
  animation-iteration-count: infinite;
  animation-duration: 1s;
}
@keyframes rotate {
  from {
    -webkit-transform: rotate(0deg);
    -ms-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  to {
    -webkit-transform: rotate(360deg);
    -ms-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
.load-leave-active {
  opacity: 1;
  transition: .5s;
}
.load-leave-to {
  opacity: 0;
}

@keyframes slideInDown {
  from {
    opacity: 0;
    transform: translate3d(0, -150%, 0);
    visibility: visible;
  }
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

@media screen and (max-width: 480px) {
  .figuremask .maskbox {
    border-width: 1px;
    background-image: url('../assets/images/urban_renewal_before_m.jpg');
  }
  .figuremask .maskbox:before {
    width: 1px;
  }
  .figuremask:before,
  .figuremask:after {
    top: 0;
  }
  .figuremask ul li,
  .figuremask ul li:nth-child(5)
  {
    width: 13%;
    margin: 0 0.64%;
  }
  .figuremask .centericon {
    width: 40px;
    height: 40px;
    border-width: 2px;
    font-size: 20px;
    transform: translate(-50%, 0) rotate(90deg);
  }
}

</style>

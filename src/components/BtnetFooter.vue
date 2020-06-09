<template>
  <footer class="btnet-footer">
    <div class="wrapper">
      <p>
        <small>內容監製：今周刊<br />專題製作｜今周刊&nbsp;&nbsp;編輯部、數位內容部</small>
      </p>
      <hr />
      <p>
        <small>數位Copyright © {{ year }}今周刊. Business Today All rights reserved.版權所有，禁止擅自轉貼節錄</small>
      </p>
    </div>
    
    <transition>
      <button v-if="goTop" v-show="showButton" @click="backTop(500)"><i class="fa fa-chevron-circle-up" /></button>
    </transition>
  </footer>
</template>

<script>
export default {
  props: {
    goTop: {
      type: Boolean,
      default: true
    },
  },
  data() {
    return {
      year: new Date().getFullYear(),
      showButton: false,
    }
  },
  created () {
    if(this.goTop) window.addEventListener('scroll', this.handleScroll);
  },
  methods: {
    backTop (duration) {
      if (document.scrollingElement.scrollTop === 0) return;
      const totalScrollDistance = document.scrollingElement.scrollTop;
      let scrollY = totalScrollDistance, oldTimestamp = null;

      function step (newTimestamp) {
        if (oldTimestamp !== null) {
          scrollY -= totalScrollDistance * (newTimestamp - oldTimestamp) / duration;
          if (scrollY <= 0) return document.scrollingElement.scrollTop = 0;
          document.scrollingElement.scrollTop = scrollY;
        }
        oldTimestamp = newTimestamp;
        window.requestAnimationFrame(step);
      }
      window.requestAnimationFrame(step);
    },
    handleScroll () {
      if (window.scrollY > (window.innerHeight / 2)) {
        this.showButton = true;
      } else {
        this.showButton = false;
      }
    }
  },
  destroyed () {
    if(this.goTop) window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style>
.btnet-footer {
  background: #4b4b4b;
}
.btnet-footer .wrapper {
  padding: 1em 0;
}
.btnet-footer p {
  margin: 0;
}
.btnet-footer small {
  color: white;
  font-size: 0.9em;
}
.btnet-footer button {
  display: block;
  padding: 0;
  margin: 0;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 50px;
  position: fixed;
  right: 1em;
  bottom: 1rem;
  color: #ffc000;
  z-index: 99;
}
.btnet-footer button i {
  display: block;
  opacity: 1;
  transition: .5s;
}
.v-leave {
  opacity: 1;
}
.v-leave-active {
  transition: .5s
}
.v-leave-to {
  opacity: 0;
}
.v-enter {
  opacity: 0;
}
.v-enter-active {
  transition: .5s
}
.v-enter-to {
  opacity: 1;
}

@media (hover: hover) {
  .btnet-footer button i:hover {
    opacity: .7;
  }
}

@media screen and (max-width: 768px) {
  .btnet-footer button {
    font-size: 45px;
    right: 1rem;
    bottom: 0.5rem;
  }
}

</style>

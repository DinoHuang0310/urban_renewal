<template>
  <li>
    <figure
      @mouseover="handleHover(true)"
      @mouseleave="handleHover(false)"
      @click="handleClick"
    >
      <div><img :src="caselist.image" :alt="caselist.title" /></div>
      <figcaption
        :class="showContent ? 'active' : ''"
        @click.stop="handleClick"
      >
        <h3>{{ caselist.title }}</h3>
        <p>{{ caselist.article }}</p>
      </figcaption>
    </figure>
  </li>
</template>

<script>
export default {
  props: {
    caselist: {
      type: Object,
      required: true,
    },
    isMobile: {
      type: Boolean,
      requiredtrue: true
    }
  },
  data() {
    return {
      showContent: false
    }
  },
  methods: {
    handleHover(changeState) {
      if(!this.isMobile) this.showContent = changeState;
    },
    handleClick() {
      if(this.isMobile) this.showContent = !this.showContent;
    },
  }
}
</script>

<style>
.case ul {
  display: flex;
  justify-content: space-around;
  margin: 4em 0;
}
.case ul li {
  width: 30%;
}
.case ul li figure {
  position: relative;
  overflow: hidden;
  cursor: pointer;
}
.case ul li img {
  display: block;
}
.case ul li figure figcaption {
  position: absolute;
  background: rgba(211, 222, 231, .75);
  width: 100%;
  height: 100%;
  left: 0;
  bottom: 0;
  padding: 1em;
  overflow: auto;
  transform: translate(0, 100%);
  transition: .5s;
}
.case ul li figure figcaption.active {
  transform: translate(0, 0);
}
.case ul li figure figcaption h3 {
  font-size: 1.4em;
  margin: 0 0 0.5em 0;
  color: #0087cd;
}
.case ul li figure figcaption h3:before {
  content: '>';
  display: inline-block;
  margin-right: 0.4em;
}
.case ul li figure figcaption p {
  margin-top: 0;
}

@media screen and (max-width: 1024px) {
  .case ul li figure figcaption {
    padding: 0.5em;
  }
  .case ul li figure figcaption h3 {
    font-size: 1.2em;
    margin-bottom: 0.5em;
  }
}

@media screen and (max-width: 768px) {
  .case ul {
    margin: 2em 0;
    justify-content: space-between;
  }
  .case ul li {
    width: 32%;
  }
  .case ul li figure figcaption {
    font-size: .9em;
  }
  .case ul li figure figcaption h3 {
    margin-bottom: 0;
  }
}

@media screen and (max-width: 767px) {
  .case ul {
    flex-wrap: wrap;
    margin: 0;
  }
  .case ul li {
    width: 48%;
    margin: 1em 0;
  }
}

@media screen and (max-width: 480px) {
  .case ul {
    display: block;
    margin: 1em 0;
  }
  .case ul li {
    width: 100%;
  }
  .case ul li figure figcaption {
    color: white;
    height: auto;
    background: rgba(0, 0, 0, .7);
    transform: none;
  }
  .case ul li figure figcaption h3 {
    font-size: 1.3em;
    color: white;
    margin-bottom: 0.2em;
  }
  .case ul li figure figcaption p {
    margin: 0;
  }
}

</style>

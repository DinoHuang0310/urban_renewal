<template>
  <div class="area">
    <h2 v-if="content.title">{{ content.title }}</h2>
    <div class="maincontent-box">
      <div v-html="content.article" />
      <div data-aos="fade-left">
        <img v-if="content.image" :src="content.image" />
      </div>
    </div>
    <div
      v-if="content.url"
      class="readmore"
    >
      <a :href="content.url" target="_blank">看完整文章</a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>
.maincontent-box {
  display: flex;
  align-items: center;
  overflow: hidden;
}
.maincontent-box > div {
  width: 50%;
  padding: 0 2em;
}
.maincontent-box > div img {
  display: block;
  margin: 0 auto;
}

@media screen and (max-width: 768px) {
  .maincontent-box {
    display: block;
  }
  .maincontent-box > div {
    width: 100%;
  }
  .maincontent-box > div img {
    width: 321px;
  }
}

@media screen and (max-width: 480px) {
  .maincontent-box {
    display: flex;
    flex-wrap: wrap-reverse;
  }
  .maincontent-box > div {
    padding: 0;
  }
}

</style>

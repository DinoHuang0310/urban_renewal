<template>
  <div class="btnetSlider">
    <swiper ref="mySwiper" :options="swiperOptions">
      <swiper-slide
        v-for="list in sliderData"
        :key="list.index"
      >
        <a :href="list.url" target="_blank">
          <figure>
            <div :class="list.isMedia ? 'btnet-slider-mediabox' : ''" >
              <img :src="list.image" :alt="list.title" />
            </div>
            <figcaption><span>{{ list.title }}</span></figcaption>
          </figure>
        </a>
      </swiper-slide>
    </swiper>
    <div class="swiper-button-prev" slot="button-prev" />
    <div class="swiper-button-next" slot="button-next" />
    <!-- <div class="swiper-pagination" slot="pagination"></div> -->
  </div>
</template>

<script>
import { Swiper, SwiperSlide, directive } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'

export default {
  name: 'BtnetSlider',
  props: {
    sliderData: {
      type: Array,
      required: true
    },
  },
  components: {
    Swiper,
    SwiperSlide
  },
  directives: {
    swiper: directive
  },
  data() {
    return {
      swiperOptions: {
        centeredSlides: true,
        loop: true,
        slidesPerView: 1,
        autoplay: {
          delay: 3000,
        },
        speed: 500,
        autoHeight: true,
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev'
        },
        // pagination: {
        //   el: '.swiper-pagination'
        // },
        spaceBetween: 20,
        breakpoints: {
          481: {
            slidesPerView: 3,
            spaceBetween: 40
          },
          1600: {
            slidesPerView: 4,
            spaceBetween: 60
          }
        }
      }
    }
  },
}
</script>

<style>
.btnetSlider {
  position: relative;
  background: #efefef;
  padding: 5em 2.5%;
}
.btnetSlider .swiper-container {
  margin: 0 50px;
}
.btnet-slider-mediabox {
  position: relative;
}
.btnet-slider-mediabox:before {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, .6);
  transition: .5s;
}
.btnet-slider-mediabox:after {
  content: '\f04b';
  font: normal normal normal 14px/1 FontAwesome;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  width: 50px;
  height: 50px;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  margin: auto;
  color: white;
  border: solid 2px white;
  border-radius: 50%;
  box-shadow: 0 0 15px rgba(0, 0, 0, .5);
  text-shadow: 0 0 15px rgba(0, 0, 0, .5);
  opacity: .6;
  transition: .5s;
}
.btnetSlider figure {
  position: relative;
}
.btnetSlider figcaption {
  padding: 0.5em 0;
  text-align: left;
  opacity: 1;
  transition: .5s;
}
.btnetSlider figcaption span {
  width: 100%;
  display: -webkit-box;
  max-height: 44.2px;
  font-size: 17px;
  line-height: 1.3;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: normal;
}
.swiper-slide > a {
  display: block;
}
.btnetSlider .swiper-button-prev,
.btnetSlider .swiper-button-next {
  outline: none;
  color: black;
}
.swiper-slide img {
  display: block;
  width: 100%;
}
.swiper-pagination {
  transform: translate3d(0, 100%, 0);
  width: 100%;
}
.swiper-pagination-bullet {
  margin: 0.4em;
}

@media (hover: hover) {
  .swiper-slide > a:hover .btnet-slider-mediabox:before {
    background: rgba(0, 0, 0, .75);
  }
  .swiper-slide > a:hover .btnet-slider-mediabox:after {
    opacity: 1;
    box-shadow: 0 0 15px rgba(255, 255, 255, .5);
    text-shadow: 0 0 15px rgba(255, 255, 255, .5);
  }
  .btnetSlider .swiper-slide > a:hover figcaption {
    opacity: .7;
  }
}

@media screen and (max-width: 640px) {
  .btnetSlider {
    padding: 3em 2.5%;
  }
}

</style>

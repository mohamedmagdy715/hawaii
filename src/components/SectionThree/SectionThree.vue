<template>
  <div class="container">
    <div class="title">Section 3</div>
    <div class="swiper-container thumb-example">
      <swiper :options="swiperOptionTop" class="swiper gallery-top" ref="swiperTop">
        <swiper-slide
          v-for="(slide, index) in swiperSlides"
          :key="index"
          :class="'slide-' + slide.id"
        >
          <img :src="slide.url" :alt="slide.id"/>
        </swiper-slide>
        <div
          class="swiper-button-next swiper-button-white"
          slot="button-next"
        ></div>
        <div
          class="swiper-button-prev swiper-button-white"
          slot="button-prev"
        ></div>
      </swiper>
      <!-- swiper2 Thumbs -->
      <swiper
        :options="swiperOptionThumbs"
        class="swiper gallery-thumbs"
        ref="swiperThumbs"
      >
        <swiper-slide
          v-for="(slide, index) in swiperSlides"
          :key="index"
          :class="'slide-' + slide.id"
        >
          <img :src="slide.thumbnailUrl" :alt="slide.id">
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/css/swiper.css";

export default {
  name: "SectionThree",
  components: {
    Swiper,
    SwiperSlide,
  },
  data() {
    return {
      swiperSlides:[],
      swiperOptionTop: {
        loop: true,
        loopedSlides: 50, // looped slides should be the same
        spaceBetween: 10,
        navigation: {
          nextEl: ".swiper-button-next",
          prevEl: ".swiper-button-prev",
        },
      },
      swiperOptionThumbs: {
        loop: true,
        loopedSlides: 50, // looped slides should be the same
        spaceBetween: 10,
        centeredSlides: true,
        slidesPerView: "auto",
        touchRatio: 0.2,
        slideToClickedSlide: true,
      },
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.getTodo()
      const swiperTop = this.$refs.swiperTop.$swiper;
      const swiperThumbs = this.$refs.swiperThumbs.$swiper;
      swiperTop.controller.control = swiperThumbs;
      swiperThumbs.controller.control = swiperTop;
    });
  },
  methods: {
    async getTodo() {
      const resp = await axios.get(
        "https://jsonplaceholder.typicode.com/photos?albumId=1"
      );
      this.swiperSlides = resp.data;
    },
  },
};
</script>

<style lang="scss" scoped>
img {
  max-width: 100%;
  height: auto;
  border-radius: 2%;
}
.title {
  font-weight: bolder;
  font-size: 2rem;
  margin-bottom: 5%;
}
.container {
  padding: 5% 0;
  text-align: center;
}
.swiper-container {
  width: 40%;
  margin: auto;
}
.thumb-example {
  height: auto;
}
.swiper {
  &.gallery-top {
    height: auto;
    width: 100%;
  }
  &.gallery-thumbs {
    margin-top: 2%;
    width: 100%;
    height: auto;
    box-sizing: border-box;
    padding: 0;
  }
  &.gallery-thumbs .swiper-slide {
    width: 25%;
    height: 100%;
    opacity: 0.7;
  }
  &.gallery-thumbs .swiper-slide-active {
    opacity: 1;
  }
}
  @media only screen and (max-width: 1200px) {
        .swiper-container {
          width: 60%;
          }
    }
    @media only screen and (max-width: 800px) {
          .swiper-container {
              width: 90%;
            }
      }
</style>

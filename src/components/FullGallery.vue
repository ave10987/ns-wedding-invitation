<template>
  <swiper :options="gallerySwiperOption" class="full-screen-swiper" :style="{ height: `${galleryHeight}px` }">
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_01.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_02.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_03.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_04.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_05.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_06.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_07.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_08.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_09.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_10.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_11.jpg" alt="">
      </div>
    </swiper-slide>
    <swiper-slide @click.prevent.stop>
      <div>
        <img src="../../static/image/page3_12.jpg" alt="">
      </div>
    </swiper-slide>
  </swiper>
</template>
<script>
export default {
  name: 'FullGallery',
  props: [
    'selectedImageIdx',
  ],
  data() {
    return {
      gallerySwiperOption: {
        // spaceBetween: 30,
        effect: 'coverflow',
        grabCursor: true,
        loop: true,
        zoom: false,
        centeredSlides: true,
        slidesPerView: 'auto',
        coverflowEffect: {
          rotate: 50,
          stretch: 0,
          depth: 100,
          modifier: 1,
          slideShadows: true,
        },
      },
    };
  },
  computed: {
    galleryHeight() {
      return window.document.documentElement.clientHeight * 0.9;
    },
  },
  mounted() {
    const gallerySwiper = document.querySelector('.full-screen-swiper.swiper-container').swiper;
    gallerySwiper.slideTo(this.selectedImageIdx, 0);
    gallerySwiper.on('resize', () => {
      this.clientHeight = document.documentElement.clientHeight;
    });
  },
};
</script>

<style>
.full-screen-swiper {
  width: 100%;
}
.full-screen-swiper .swiper-slide {
  background-size: contain;
  background-repeat: no-repeat;
  text-align: center;
}

.full-screen-swiper div {
  position: relative;
  height: 100%;
}

.full-screen-swiper img {
  width: 100%;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}
</style>

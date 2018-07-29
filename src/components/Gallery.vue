<template>
  <swiper :options="verticalSwiperOption" class="third gallery-vertical-swiper" :style="{height: `${swiperHeight}px`}">
    <swiper-slide style="box-sizing: border-box; -webkit-box-sizing: border-box; height: auto;">
      <grid-layout
        :layout="layout"
        :col-num="4"
        :row-height="30"
        :is-draggable="false"
        :is-resizable="false"
        :is-mirrored="false"
        :vertical-compact="true"
        :margin="[10, 10]"
      >
        <grid-item
          v-for="(item, index) in layout"
          :key="index"
          :x="item.x"
          :y="item.y"
          :w="item.w"
          :h="item.h"
          :i="item.i">
            <img :data-src="item.src" alt="" style="width:100%; height:100%;" @click="onClickImage" :data-index="index" class="swiper-lazy">
        </grid-item>
      </grid-layout>
    </swiper-slide>
  </swiper>
</template>
<script>
import { GridLayout, GridItem } from 'vue-grid-layout';

export default {
  name: 'Gallery',
  components: {
    GridLayout,
    GridItem,
  },
  data() {
    return {
      clientHeight: document.documentElement.clientHeight,
      verticalSwiperOption: {
        direction: 'vertical',
        slidesPerView: 'auto',
        freeMode: true,
        mousewheel: true,
      },
      layout: [
        { x: 0, y: 0, w: 2, h: 3, i: '1', src: '../../static/image/second.jpg' },
        { x: 2, y: 0, w: 2, h: 6, i: '2', src: '../../static/image/first_background.jpg' },
        { x: 0, y: 3, w: 2, h: 6, i: '3', src: 'https://dummyimage.com/600x400/000/fff' },
        { x: 2, y: 6, w: 2, h: 6, i: '4', src: 'https://dummyimage.com/600x400/000/fff' },
        { x: 0, y: 9, w: 2, h: 6, i: '5', src: 'https://dummyimage.com/600x400/000/fff' },
        { x: 2, y: 12, w: 2, h: 3, i: '6', src: 'https://dummyimage.com/600x400/000/fff' },
        { x: 0, y: 15, w: 2, h: 6, i: '7', src: 'https://dummyimage.com/600x400/000/fff' },
        { x: 2, y: 15, w: 2, h: 6, i: '8', src: 'https://dummyimage.com/600x400/000/fff' },
        { x: 0, y: 21, w: 4, h: 6, i: '9', src: 'https://dummyimage.com/600x400/000/fff' },
      ],
    };
  },
  computed: {
    swiperHeight() {
      return this.clientHeight * 0.75;
    },
  },
  methods: {
    onClickImage(e) {
      this.$EventBus.$emit('galleryOpen', e.target.getAttribute('data-index'));
    },
  },
  mounted() {
    const gallerySwiper = document.querySelector('.gallery-vertical-swiper.swiper-container').swiper;
    gallerySwiper.on('resize', () => {
      this.clientHeight = document.documentElement.clientHeight;
    });
  },
};
</script>

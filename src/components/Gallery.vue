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
        class="grid-layout"
      >
        <grid-item
          style="overflow: hidden;"
          v-for="(item, index) in layout"
          :key="index"
          :x="item.x"
          :y="item.y"
          :w="item.w"
          :h="item.h"
          :i="item.i">
            <img :data-src="item.src" alt="" style="width:100%; position: absolute; top: 0; bottom: 0; margin: auto;" @click="onClickImage" :data-index="index" class="swiper-lazy">
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
        { x: 0, y: 0, w: 2, h: 3, i: '1', src: '../../static/image/page3_01.jpg' },
        { x: 2, y: 0, w: 2, h: 6, i: '2', src: '../../static/image/page3_02.jpg' },
        { x: 0, y: 3, w: 2, h: 6, i: '3', src: '../../static/image/page3_03.jpg' },
        { x: 2, y: 6, w: 2, h: 6, i: '4', src: '../../static/image/page3_04.jpg' },
        { x: 0, y: 9, w: 2, h: 6, i: '5', src: '../../static/image/page3_05.jpg' },
        { x: 2, y: 12, w: 2, h: 3, i: '6', src: '../../static/image/page3_06.jpg' },
        { x: 0, y: 15, w: 2, h: 3, i: '7', src: '../../static/image/page3_07.jpg' },
        { x: 2, y: 15, w: 2, h: 6, i: '8', src: '../../static/image/page3_08.jpg' },
        { x: 0, y: 18, w: 2, h: 6, i: '9', src: '../../static/image/page3_09.jpg' },
        { x: 2, y: 21, w: 2, h: 6, i: '10', src: '../../static/image/page3_10.jpg' },
        { x: 0, y: 24, w: 2, h: 6, i: '11', src: '../../static/image/page3_11.jpg' },
        { x: 2, y: 27, w: 2, h: 3, i: '12', src: '../../static/image/page3_12.jpg' },
      ],
    };
  },
  computed: {
    swiperHeight() {
      return this.clientHeight * 0.9;
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

<style>
  .third {
    margin-top: 10%;
  }
  .grid-layout {
    margin-top: -10px;
  }
</style>


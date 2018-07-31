<template>
  <div class="container">
    <div class="dimmed" v-if="isGalleryOpen" @click.prevent.stop="closeGallery">
      <span @click.prevent="closeGallery" style="background-size: contain; background-image: url('../../static/image/close.png'); width: 30px; height: 30px; float: right; margin: 10px;"></span>
      <FullGallery :selectedImageIdx="selectedImageIdx"/>
    </div>
    <swiper class="swiper-wrapper" :options="mainSwiperOption">
      <swiper-slide>
        <First />
      </swiper-slide>
      <swiper-slide>
        <Second />
      </swiper-slide>
      <swiper-slide>
        <Gallery />
      </swiper-slide>
      <swiper-slide>
        <Map />
      </swiper-slide>
    </swiper>
  </div>
</template>
<script>
import First from '@/components/First';
import Second from '@/components/Second';
import Gallery from '@/components/Gallery';
import FullGallery from '@/components/FullGallery';
import Map from '@/components/Map';

export default {
  name: 'Home',
  components: {
    First,
    Second,
    Gallery,
    FullGallery,
    Map,
  },
  data() {
    return {
      mainSwiperOption: {
        lazy: {
          loadPrevNext: true,
          loadPrevNextAmount: 1,
        },
      },
      isGalleryOpen: false,
      selectedImageIdx: 0,
    };
  },
  methods: {
    closeGallery() {
      this.isGalleryOpen = false;
    },
  },
  mounted() {
    this.$EventBus.$on('galleryOpen', (index) => {
      this.isGalleryOpen = true;
      this.selectedImageIdx = index;
    });
  },
};
</script>

<template>
  <div class="keepcalm-font first container">
    <img class="background" src="../../static/image/first_background.jpg" alt="" @load="backgroundLoaded">
    <div class="title">
      <div class="text-container">
        <div class="text-vertical-middle">
          <div class="crown">^</div>
          <div class="text1">KEEP<br />CALM</div>
          <div class="text2">WE ARE</div>
          <div class="text1">GETTING<br />MARRIED</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'First',
  data() {
    return {
      isBackgroundLoaded: false,
    };
  },
  methods: {
    backgroundLoaded(e) {
      this.isBackgroundLoaded = true;
      document.querySelector('.first .title').style.height = `${e.target.clientHeight}px`;
    },
  },
};
</script>


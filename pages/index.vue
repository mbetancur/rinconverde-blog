<template>
  <div class="container">
    <div class="container__video">
      <video
        :src="require('@/static/videos/video.mp4')"
        autoplay
        loop
        playsinline
        muted
        preload="auto"
        :poster="require('@/static/images/poster.jpg')"
      ></video>
      <Logo />
      <div class="links">
        <NuxtLink class="button--green" to="/blog"> Blog </NuxtLink>
      </div>
    </div>
    <Carousel class="container__carousel" />
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
export default {
  components: {
    Carousel,
  },
};
</script>

<style lang="scss">
.container {
  .container__video {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;

    video {
      z-index: -1;
      object-fit: cover;
      width: 100vw;
      height: 100vh;
      position: fixed;
      top: 0;
      left: 0;
    }
    .links {
      padding-top: 15px;
    }
  }

  .container__carousel {
    padding-top: 45px;
  }
}
</style>

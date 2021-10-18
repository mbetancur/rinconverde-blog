<template>
  <div class="container">
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
    <carousel
      :scrollPerPage="true"
      :perPageCustom="[
        [480, 2],
        [768, 4],
      ]"
    >
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 2 Content
      </slide>
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 1 Content
      </slide>
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 3 Content
      </slide>
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 4 Content
      </slide>
    </carousel>
  </div>
</template>
<script>
import { Carousel, Slide } from "vue-carousel";
export default {
  components: {
    Carousel,
    Slide,
  },
};
</script>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  video {
    z-index: -1;
    object-fit: cover;
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
  }
}

.links {
  padding-top: 15px;
}
</style>

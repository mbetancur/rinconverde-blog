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
    <Carousel class="container__carousel">
      <slide
        :key="project.title"
        class="carousel__slide"
        v-for="project of projects"
      >
        <NuxtLink
          :to="{ name: 'project-slug', params: { slug: project.slug } }"
          class="project__link"
        >
          <img class="carousel__image" :src="project.mainImage" />
          <i> {{ project.title }}</i>
        </NuxtLink>
      </slide>
    </Carousel>
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
import { Slide } from "vue-carousel";

export default {
  components: {
    Carousel,
    Slide,
  },
  async asyncData({ $content, params }) {
    const projects = await $content("project", params.slug)
      .only(["title", "mainImage", "slug"])
      .fetch();
    return { projects };
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
    padding: 45px 0;
  }
}
</style>

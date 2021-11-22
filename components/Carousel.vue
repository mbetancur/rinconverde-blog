<template>
  <carousel
    class="carousel"
    autoplay
    autoplayHoverPause
    :autoplayTimeout="5000"
    scrollPerPage
    loop
    mouseDrag
    :speed="4000"
    :perPageCustom="[
      [100, 1],
      [768, 3],
    ]"
  >
    <slide
      :key="project.title"
      class="carousel__slide"
      v-for="project of projects"
    >
      <img class="carousel__image" :src="project.mainImage" />
      <i> {{ project.title }}</i>
    </slide>
  </carousel>
</template>

<script>
import { Carousel, Slide } from "vue-carousel";
export default {
  components: {
    Carousel,
    Slide,
  },
  props: {
    projects: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style lang="scss">
.carousel {
  background-color: ivory;
  &__image {
    padding: 12px;
    max-width: 100%;
  }
}
</style>
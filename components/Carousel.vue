<template>
  <carousel
    class="carousel"
    autoplay
    autoplayHoverPause
    :autoplayTimeout="5000"
    scrollPerPage
    loop
    mouseDrag
    :speed="transitionSpeed"
    :perPageCustom="[
      [100, 1],
      [768, 3],
    ]"
  >
    <slot></slot>
  </carousel>
</template>
<script>
//TODO recieve props for diffrent carousel implementations
import { Carousel } from "vue-carousel";
export default {
  components: {
    Carousel,
  },
  props: {
    transitionSpeed: {
      type: Number,
      default: 3000,
    },
  },
};
</script>

<style lang="scss">
.carousel {
  background-color: ivory;
  &__slide {
    padding: 6px;
  }
  &__image {
    max-width: 100%;
  }
}
</style>
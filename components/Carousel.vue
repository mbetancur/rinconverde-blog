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
};
</script>

<style lang="scss">
.carousel {
  background-color: ivory;
  &__image {
    padding: 6px;
    max-width: 100%;
  }
}
</style>
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
    <slide class="carousel__slide">
      <img
        class="carousel__image"
        :src="require('@/static/images/thumbnails/el-salado.jpg')"
      />
    </slide>
    <slide>
      <img
        class="carousel__image"
        :src="require('@/static/images/thumbnails/el-salado.jpg')"
      />
    </slide>
    <slide>
      <img
        class="carousel__image"
        :src="require('@/static/images/thumbnails/el-salado.jpg')"
      />
    </slide>
    <slide>
      <img
        class="carousel__image"
        :src="require('@/static/images/thumbnails/el-salado.jpg')"
      />
    </slide>
    <slide>
      <img
        class="carousel__image"
        :src="require('@/static/images/thumbnails/el-salado.jpg')"
      />
    </slide>
    <slide>
      <img
        class="carousel__image"
        :src="require('@/static/images/thumbnails/el-salado.jpg')"
      />
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
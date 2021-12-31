<template>
  <div class="project">
    <!-- TODO: wtf with the font size ??? .. check blog title  -->
    <h1 class="project__title">{{ project.title }}</h1>
    <Carousel class="container__carousel" :transitionSpeed="4000">
      <slide :key="image.name" class="carousel__slide" v-for="image of images">
        <img class="carousel__image" :src="image.picture" />
        <i> {{ image.name }} </i>
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
  computed: {
    images() {
      return this.project.images;
    },
  },
  async asyncData({ $content, params }) {
    const project = await $content("project", params.slug)
      .only(["title", "images"])
      .where({ slug: params.slug })
      .fetch();
    return { project };
  },
};
</script>

<style lang="scss" scoped>
.project {
  &__title {
    margin: 1rem;
  }
  .container__carousel {
    margin-top: 6rem;
  }
}
</style>
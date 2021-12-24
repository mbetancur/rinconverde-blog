<template>
  <div>
    {{ project.title }}
    <Carousel class="container__carousel">
      <slide :key="image.name" class="carousel__slide" v-for="image of images">
        <img class="carousel__image" :src="image.picture" />
        <i> {{ image.name }}</i>
      </slide>
    </Carousel>
  </div>
</template>

<script>
import { Slide } from "vue-carousel";

export default {
  components: {
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
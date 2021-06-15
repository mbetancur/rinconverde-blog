<template>
  <article class="post">
    <custom-image class="post_image" :image="post.img" :alt="post.alt" />
    <h1>{{ post.title }}</h1>
    <nuxt-content :document="post" />
  </article>
</template>

<script>
import CustomImage from "@/components/CustomImage.vue";
export default {
  components: {
    CustomImage,
  },
  async asyncData({ $content, params }) {
    const post = await $content("post", params.post).fetch();
    return { post };
  },
};
</script>

<style lang="scss" >
.post {
  display: flex;
  flex-flow: column;
  align-items: center;

  &_image {
    // max-width: 100%;
  }
}
</style>
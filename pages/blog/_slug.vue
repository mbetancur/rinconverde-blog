<template>
  <article class="post">
    <h1 class="post_title">{{ post.title }}</h1>
    <custom-image class="post_image" :image="post.img" :alt="post.alt" />
    <nuxt-content class="post_content" :document="post" />
  </article>
</template>

<script>
import CustomImage from "@/components/CustomImage.vue";
export default {
  components: {
    CustomImage,
  },
  async asyncData({ $content, params }) {
    const post = await $content("post", params.slug).fetch();
    return { post };
  },
};
</script>

<style lang="scss" >
.post {
  display: flex;
  flex-flow: column;
  align-items: center;
  &_title {
    margin: 1rem 0;
  }
  &_image {
    width: 100%;
  }
  &_content {
    margin: 1.2em;
  }
}
</style>
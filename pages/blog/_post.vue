<template>
  <article class="post">
    <img :src="require(`~/static/images/${post.img}`)" :alt="post.alt" />
    <h1>{{ post.title }}</h1>
    <nuxt-content :document="post" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content("posts", params.post).fetch();
    return { post };
  },
};
</script>

<style>
.post {
  display: flex;
  flex-flow: column;
  align-items: center;
}
</style>
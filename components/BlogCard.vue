<template>
  <li class="blog-card">
    <NuxtLink :to="post.path">
      <img
        :src="require(`~/static/images/thumbnails/${post.img}`)"
        :alt="post.alt"
      />
      <div>
        <h2 class="blog-card__title">{{ post.title }}</h2>
        <p class="blog-card__description">{{ post.description }}</p>
      </div>
    </NuxtLink>
  </li>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.blog-card {
  a {
    text-decoration: none;
  }
  &__title {
    color: #030303;
  }
  &__description {
    color: #767676;
  }
}
</style>
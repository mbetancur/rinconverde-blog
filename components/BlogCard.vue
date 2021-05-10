<template>
  <li class="blog-card">
    <NuxtLink :to="post.path" class="blog-card__link">
      <img
        class="blog-card__image"
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
  padding: 1rem 0;
  &__link {
    color: #030303;
    &:hover {
      color: green;
    }
    &:active {
      color: green;
    }
    text-decoration: none;
  }
  &__image {
    max-width: 500px;
    width: 100%;
  }
  &__description {
    padding: 0.3rem 0;
    color: #767676;
  }
}
</style>
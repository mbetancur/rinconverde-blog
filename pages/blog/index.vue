<template>
  <div class="blogs">
    <h1>Blog Posts</h1>
    <ul class="blog-cards">
      <blog-card
        class="blog-card"
        :key="post.slug"
        v-for="post of posts"
        :post="post"
      />
    </ul>
  </div>
</template>

<script>
import BlogCard from "@/components/BlogCard";
export default {
  components: {
    BlogCard,
  },
  async asyncData({ $content }) {
    const posts = await $content("post")
      .only(["title", "description", "img", "slug"])
      .sortBy("createdAt", "asc")
      .fetch();
    return {
      posts,
    };
  },
};
</script>

<style lang="scss" >
.blogs {
  padding: 0.6rem;

  .blog-cards {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    padding-left: 0;
    list-style-type: none;
  }
}
</style>
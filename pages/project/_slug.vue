<template>
  <div>
    {{ project.title }}
    <Carousel class="container__carousel" :projects="project[0]" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const project = await $content("project", params.slug)
      .only(["title", "images"])
      .where({ title: "Cisneros" })
      .fetch();
    return { project };
  },
};
</script>

<style lang="scss" >
</style>
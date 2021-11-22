<template>
  <img :src="project[0].images[0]" alt="" />
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const project = await $content("project", params.slug).fetch();
    console.log(project[0].images[0]);
    return { project };
  },
};
</script>

<style lang="scss" >
</style>
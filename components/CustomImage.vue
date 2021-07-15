<template>
  <img
    :alt="alt"
    :srcset="imageSrcset"
    class="custom-image"
  />
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      required: true,
    },
    alt: {
      type: String,
      required: true,
    },
  },
  computed: {
    imageSrcset() {
      return `${require(`@/static/images/thumbnails/${this.image}`)} 1000w, ${require(`@/static/images/${this.image}`)} 5120w`;
    },
  },
};
</script>

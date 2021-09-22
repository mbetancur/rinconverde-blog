<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">El Rincon Verde</h1>
      <div class="links">
        <NuxtLink class="button--green" to="/blog"> Blog </NuxtLink>
      </div>
    </div>
    <carousel
      :scrollPerPage="true"
      :perPageCustom="[
        [480, 2],
        [768, 4],
      ]"
    >
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 2 Content
      </slide>
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 1 Content
      </slide>
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 3 Content
      </slide>
      <slide>
        <img
          src="https://picsum.photos/300/100/"
          style="width: 300px; max-width: 100%"
        />Slide 4 Content
      </slide>
    </carousel>
  </div>
</template>
<script>
import { Carousel, Slide } from "vue-carousel";
export default {
  components: {
    Carousel,
    Slide,
  },
};
</script>
<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

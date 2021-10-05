<template>
  <div class="container">
    <video
      :src="require('@/static/videos/hero-bg.mp4')"
      autoplay
      loop
      playsinline
      muted
    ></video>
    <Logo />
    <div class="links">
      <NuxtLink class="button--green" to="/blog"> Blog </NuxtLink>
    </div>
  </div>
</template>

<style lang="scss">
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  video {
    z-index: -1;
    object-fit: cover;
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
  }
}

.links {
  padding-top: 15px;
}
</style>

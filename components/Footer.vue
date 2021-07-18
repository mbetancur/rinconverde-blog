<template>
  <p class="footer">
    © 2021 — Dev-author: 
    <a href="https://twitter.com/MBetancur22">Mateo</a>
  </p>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.footer {
  @include body-style();
  bottom: 0;
  background-color: $second-color;
  padding: 50px 0;
  color: $third-color;
}
</style>
<template>
  <p class="footer">This is the footer. With some message</p>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
@mixin body-style {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.footer {
    @include body-style();
  bottom: 0;
  background-color: rgb(16, 135, 117);
  padding: 50px 0;
}
</style>
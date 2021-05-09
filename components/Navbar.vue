<template>
  <nav id="nav" class="nav-menu">
    <header class="nav-menu__header" @click="openMenu" role="button">
      <div class="nav-menu__header-line"></div>
      <div class="nav-menu__header-line"></div>
    </header>
    <div v-show="showMenu" class="nav-menu__body">
      <NuxtLink class="button--green" to="/"> Home </NuxtLink>
      <NuxtLink class="button--green" to="/blog"> Blog </NuxtLink>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false,
    };
  },
  methods: {
    openMenu() {
      this.showMenu = !this.showMenu;
    },
  },
};
</script>

<style lang="scss" scoped>
.nav-menu {
  width: 100%;

  &__header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    border-radius: 50%;
    background-color: green;
    width: 50px;
    height: 50px;
    z-index: 12;

    &-line {
      background-color: black;
      height: 3px;
      width: 25px;
      margin: 2px;
    }
  }
}
</style>
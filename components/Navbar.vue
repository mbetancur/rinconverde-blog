<template>
  <nav id="nav" class="nav-menu" v-click-outside="openMenu">
    <header class="nav-menu__header" @click="openMenu" role="button">
      <div class="nav-menu__header-line"></div>
      <div class="nav-menu__header-line"></div>
    </header>
    <div :class="[showMenu ? 'nav-menu__body' : 'nav-menu__body-close']">
      <NuxtLink class="button--green" to="/"> Home </NuxtLink>
      <NuxtLink class="button--green" to="/blog"> Blog </NuxtLink>
    </div>
  </nav>
</template>

<script>
import "@/directives";

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

    &-line {
      background-color: black;
      height: 3px;
      width: 25px;
      margin: 2px;
    }
  }

  &__body {
    position: fixed;
    transition: all 1s;
    z-index: 10000;

    &-close {
      position: fixed;
      transform: translateY(-100px);
      transition: all 1s;
    }
  }
}
</style>
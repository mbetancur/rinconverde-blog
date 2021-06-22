<template>
  <nav id="nav" class="nav-menu">
    <header class="nav-menu__header" @click="openMenu" role="button">
      <div class="nav-menu__header-line"></div>
      <div class="nav-menu__header-line"></div>
    </header>
    <div
      class="nav-menu__body"
      :class="[showMenu ? 'nav-menu__body-open' : 'nav-menu__body-close']"
    >
      <NuxtLink class="button--green" to="/"> Home </NuxtLink>
      <NuxtLink class="button--green" to="/blog"> Blog </NuxtLink>
      <NuxtLink class="button--green" to="/blog"> About </NuxtLink>
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
    closeMenu() {
      if (this.showMenu) {
        this.showMenu = false;
      }
    },
  },
  // TODO: look 4 better solution to close menu on routing navigation
  watch: {
    $route() {
      this.showMenu = false;
    },
  },
};
</script>

<style lang="scss" scoped>
@mixin body-style {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.nav-menu {
  width: 100%;

  &__header {
    @include body-style();
    border-radius: 50%;
    background-color: rgb(16, 135, 117);
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
    @include body-style();
    position: fixed;
    width: 100%;
    height: 100%;

    &-open {
      z-index: 10000;
      transition: all 0.8s;
      background-color: rgb(39, 181, 159);
    }

    &-close {
      transform: translateY(-1000px);
      transition: all 0.8s;
    }

    .button--green {
      margin: 10px;
    }
  }

  @media (min-width: 768px) {
    &__header {
      display: none;
    }
  }
}
</style>
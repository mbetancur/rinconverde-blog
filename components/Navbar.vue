<template>
  <div class="navbar">
    <input id="main-menu-checkbox" type="checkbox" v-model="checked" />
    <header>
      <label for="main-menu-checkbox" class="menu-toggle">
        <div class="burger-icon">
          <span></span>
          <span></span>
        </div>
      </label>
      <h1 class="logo">El Rincón Verde</h1>
      <nav
        id="main-menu"
        role="navigation"
        class="main-menu"
        aria-expanded="false"
        aria-label="Main menu"
      >
        <label for="main-menu-checkbox" class="menu-close">
          <div class="close-icon"></div>
        </label>
        <ul>
          <li><NuxtLink to="/"> Home </NuxtLink></li>
          <li><NuxtLink to="/blog">Blog</NuxtLink></li>
        </ul>
      </nav>
      <label
        for="main-menu-checkbox"
        class="backdrop"
        tabindex="-1"
        aria-hidden="true"
        hidden
      ></label>
    </header>
  </div>
</template>

<script>
export default {
  data() {
    return {
      checked: false,
    };
  },
  // TODO: look 4 better solution to close menu on routing navigation
  watch: {
    $route() {
      this.checked = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.close-icon:after {
  content: "";
  height: 32px;
  border-left: 6px solid $third-color;
  border-radius: 10px;
  position: absolute;
  transform: rotate(45deg);
}

.close-icon:before {
  content: "";
  height: 32px;
  border-left: 6px solid $third-color;
  border-radius: 10px;
  position: absolute;
  transform: rotate(-45deg);
}

.burger-icon {
  display: flex;
  flex-direction: column;
  width: 2.5rem;
  span {
    background-color: $second-color;
    border-radius: 10px;
    height: 0.5rem;
    margin: 4px 0;
  }
}

header {
  padding: 20px;
  display: flex;
}

/* Button styling */
.menu-toggle {
  padding: 0 15px;
  color: $second-color;
  cursor: pointer;
}

#main-menu-checkbox {
  position: absolute;
  left: -100vw; /* get it off the screen */
}

/*
 Default styles + Mobile first
 Offscreen menu style
*/
.main-menu {
  position: fixed;
  left: -200px;
  top: 0;
  height: 100vh;
  overflow-y: hidden;
  overflow-x: visible;
  transition: left 0.3s ease, box-shadow 0.3s ease;
  z-index: 999;
}

.main-menu .menu-close:first-child {
  border-bottom: none;
}

.main-menu ul {
  list-style: none;
  margin: 0;
  padding: 3em 0 0;
  -webkit-box-shadow: -8px 0 8px rgba(0, 0, 0, 0.5);
  -moz-box-shadow: -8px 0 8px rgba(0, 0, 0, 0.5);
  box-shadow: -8px 0 8px rgba(0, 0, 0, 0.5);
  min-height: 100%;
  width: 200px;
  background: $second-color;
}

.main-menu a,
.main-menu .menu-close {
  display: block;
  padding: 0.75em 35px;
  line-height: 1em;
  font-size: 1em;
  color: $third-color;
  text-decoration: none;
  border-bottom: 1px solid $main-color;
}

.main-menu li:first-child a {
  border-top: 1px solid $main-color;
}

.main-menu .menu-close {
  position: absolute;
  right: 0;
  top: 0;
  cursor: pointer;
}

/*
 On small devices, allow it to toggle...
*/
/*
 :target for non-JavaScript
 aria-expanded="true/false" will be for JavaScript
*/
#main-menu-checkbox:checked ~ header .main-menu,
.main-menu[aria-expanded="true"] {
  left: 0;
  outline: none;
  -moz-box-shadow: 3px 0 12px rgba(0, 0, 0, 0.25);
  -webkit-box-shadow: 3px 0 12px rgba(0, 0, 0, 0.25);
  box-shadow: $main-color;
}

#main-menu-checkbox:checked ~ header .menu-close,
.main-menu[aria-expanded="true"] .menu-close {
  z-index: 1001;
}

#main-menu-checkbox:checked ~ header .main-menu ul,
.main-menu[aria-expanded="true"] ul {
  position: relative;
  z-index: 1000;
}

#main-menu-checkbox:checked ~ header .backdrop,
.main-menu[aria-expanded="true"] + .backdrop {
  position: fixed;
  display: flex;
  content: "";
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 998;
  background: $main-color;
  background: rgba(0, 0, 0, 0.85);
  cursor: default;
}

/*
 Larger screen styling
 Horizontal menu
*/
@media (min-width: 768px) {
  header {
    padding: 20px;
    display: flex;
    align-items: baseline;
  }

  .menu-toggle,
  .main-menu .menu-close,
  #main-menu-checkbox {
    display: none;
  }

  /* Undo positioning of off-canvas menu */
  .main-menu {
    position: relative;
    left: auto;
    top: auto;
    height: auto;
    overflow-y: auto; /* fix dumb MS Edge scrollbar issue */
  }

  .main-menu ul {
    display: flex;
    padding: 0;
    -webkit-box-shadow: none;
    -moz-box-shadow: none;
    box-shadow: none;
    height: auto;
    width: auto;
    background: none;
  }

  .main-menu a {
    color: $main-color;
    border: 0 !important; /* Remove borders from off-canvas styling */
  }

  .main-menu a:hover,
  .main-menu a:focus {
    background: none; /* Remove background from off-canvas styling */
    color: $main-color;
  }
}

.logo {
  margin: 0 30px 0 10px;
  font-size: 1.5em;
}
</style>
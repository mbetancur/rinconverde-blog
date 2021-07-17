<template>
  <div>
    <input id="main-menu-checkbox" type="checkbox" v-model="checked" />
    <header>
      <label for="main-menu-checkbox" class="menu-toggle">
        <!-- TODO burger icon here -->
        <span class="burger-line">--</span>
        <span class="burger-line">--</span>
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
          <!-- TODO burger icon here -->
          <span class="burger-line">--</span>
          <span class="burger-line">--</span>
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
/* Button styling */
.menu-toggle {
  display: inline-block;
  padding: 0.75em 15px;
  line-height: 1em;
  font-size: 1em;
  color: #333;
  cursor: pointer;
}

.menu-toggle:hover,
#main-menu-checkbox:focus ~ header .menu-toggle {
  color: green;
  outline: auto;
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

.main-menu ul {
  list-style: none;
  margin: 0;
  padding: 2.5em 0 0;
  /* Hide shadow w/ -8px while 'closed' */
  -webkit-box-shadow: -8px 0 8px rgba(0, 0, 0, 0.5);
  -moz-box-shadow: -8px 0 8px rgba(0, 0, 0, 0.5);
  box-shadow: -8px 0 8px rgba(0, 0, 0, 0.5);
  min-height: 100%;
  width: 200px;
  background: #1a1a1a;
}

.main-menu a,
.main-menu .menu-close {
  display: block;
  padding: 0.75em 15px;
  line-height: 1em;
  font-size: 1em;
  color: #fff;
  text-decoration: none;
  border-bottom: 1px solid #383838;
}

.main-menu li:first-child a {
  border-top: 1px solid #383838;
}

.main-menu a:hover,
.main-menu a:focus,
.main-menu .menu-close:hover,
#main-menu-checkbox:focus ~ header .menu-close {
  background: #333;
  text-decoration: underline;
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
  box-shadow: 3px 0 12px rgba(0, 0, 0, 0.25);
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
  position: absolute;
  display: block;
  content: "";
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 998;
  background: #000;
  background: rgba(0, 0, 0, 0.85);
  cursor: default;
}

/*
 Larger screen styling
 Horizontal menu
*/
@media (min-width: 768px) {
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

    /* Undo off-canvas styling */
    padding: 0;
    -webkit-box-shadow: none;
    -moz-box-shadow: none;
    box-shadow: none;
    height: auto;
    width: auto;
    background: none;
  }

  .main-menu a {
    color: rgb(0, 204, 201);
    border: 0 !important; /* Remove borders from off-canvas styling */
  }

  .main-menu a:hover,
  .main-menu a:focus {
    background: none; /* Remove background from off-canvas styling */
    color: rgb(10, 204, 0);
  }
}

header {
  padding: 20px;
  display: flex;
  align-items: baseline;
}

.logo {
  margin: 0 30px 0 10px;
  font-size: 1.5em;
}
</style>
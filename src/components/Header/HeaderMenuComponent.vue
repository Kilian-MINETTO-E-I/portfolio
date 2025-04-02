<script>
  import BurgerMenuComponent from './BurgerMenuComponent.vue';
  import ListMenuComponent from './ListMenuComponent.vue';

  export default {
    components: {
      BurgerMenuComponent,
      ListMenuComponent
    },
    methods: {
      isMobile() {
        const headerMenu = document.getElementById('mobile-menu');
        if (window.innerWidth <= 768) {
          headerMenu.style.display = 'block';
        } else {
          headerMenu.style.display = 'none';
        }
      },
      openPanel() {
        const burger = document.getElementById("burger-wrapper");
        const panelMenu = document.getElementById('panel-menu');
        if (burger.classList.contains("clicked")) {
          panelMenu.style.right = "0";
        }
      },
      closePanel() {
        const burger = document.getElementById("burger-wrapper");
        const panelMenu = document.getElementById('panel-menu');
        burger.classList.remove("clicked");
        if (!burger.classList.contains("clicked")) {
          panelMenu.style.right = "100%"
        }
      }
    },
    mounted() {
      this.isMobile();
      window.addEventListener('resize', this.isMobile);
    },
    beforeUnmount() {
      window.removeEventListener('resize', this.isMobile);
    }
  }
</script>

<template>
  <div id="mobile-menu">
    <BurgerMenuComponent @click.prevent="openPanel" />
  </div>
  <div id="panel-menu" class="panel-menu-context">
    <div 
      id="cross-menu"
      @click="closePanel"
    >
      <span></span>
    </div>
    <ListMenuComponent />
  </div>
</template>

<style scoped>
#panel-menu {
  position: absolute;
  right: -100%;
  top: 0;
  width: 70%;
  height: 100vh;
  background-color: #FFFFFF;
  z-index: 3;
}

#panel-menu #links {
  display: block !important;
}

#links {
  position: absolute;
  top: 30%;
  left: 50%;
  transform: translateX(-50%);
  list-style: none;
}

#panel-menu ::v-deep a {
  font-size: 2.5rem !important;
  display: block;
  text-decoration: none;
  color: inherit;
}

#panel-menu >>> a {
  font-size: 4rem !important;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  text-wrap: nowrap;
}

#cross-menu {
  position: absolute;
  top: 4%;
  right: 10%;
  width: 50px;
  height: 50px;
  cursor: pointer;
}

#cross-menu span {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 65%;
  height: 2px;
  background-color: #000000;
  transform: rotate(45deg);
}
#cross-menu span::after {
  content: '';
  position: absolute;
  transform: rotate(-90deg);
  width: 100%;
  height: 2px;
  background-color: inherit;
}


@media screen and (width <= 768px) {
  #panel-menu >>> a {
    font-size: 2.25rem !important;
  }
}
</style>
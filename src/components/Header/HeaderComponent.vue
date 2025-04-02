<script>
  import HeaderMenuComponent from './HeaderMenuComponent.vue';
  import ListMenuComponent from './ListMenuComponent.vue';

  export default {
    components: {
      HeaderMenuComponent,
      ListMenuComponent
    },
    methods: {
      scrollToTop() {
         window.scrollTo({top: 0, behavior: 'smooth'});
      },
      isMobile() {
        const mainLinks = document.querySelector('#main-menu');
        const windowWidth = window.innerWidth;
        if (windowWidth <= 768) {
          mainLinks.style.display = 'none';
        } else {
          mainLinks.style.display = 'flex';
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
  <div id="header-wrapper">
    <a 
      id="hero-link"
      href="#hero"
      @click.prevent="scrollToTop"
    >
    Kilian MINETTO
    </a>
    <HeaderMenuComponent />
    <div id="main-menu">
      <ListMenuComponent />
    </div>
  </div>
</template>

<style scoped>
  #header-wrapper {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    list-style: none;
    z-index: 10;
  }

  #hero-link {
    color: rgba(255, 255, 255, 0.7);
    transition: color 0.2s cubic-bezier(0.6, -0.28, 0.735, 0.045);
    will-change: color;
  }

  #hero-link {
    font-weight: 700;
    font-size: 1.25rem;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    text-wrap: nowrap;
  }

  #links {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    list-style: none;
  }

  .scrolled #hero-link{
    color: #000000;
  }
</style>
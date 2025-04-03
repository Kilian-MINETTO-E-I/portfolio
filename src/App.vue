<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import HeaderComponent from "./components/Header/HeaderComponent.vue";
import HeroContentComponent from "@/components/Hero/HeroContentComponent.vue";
import AboutComponent from "./components/About/AboutComponent.vue";
import MarqueeComponent from '@/components/Projects/MarqueeComponent.vue';
import ProjectComponent from "./components/Projects/ProjectComponent.vue";
import ContactComponent from "./components/Contact/ContactComponent.vue";
import FooterComponent from "./components/Footer/FooterComponent.vue";

const isScrolled = ref(false);
const isMobileViewport = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

const checkViewport = () => {
  isMobileViewport.value = window.innerWidth <= 768;
  // Force la classe scrolled sur mobile
  if (isMobileViewport.value) {
    isScrolled.value = true;
  }
};

onMounted(() => {
  checkViewport(); // Vérification initiale
  window.addEventListener('scroll', handleScroll);
  window.addEventListener('resize', checkViewport);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
  window.removeEventListener('resize', checkViewport);
});
</script>

<template>
  
  <header :class="{'scrolled': isScrolled || isMobileViewport}">
    <HeaderComponent />
  </header>
  <main>
    <section id="hero">
      <HeroContentComponent />
    </section>
    <section id="about">
      <AboutComponent />
    </section>
    <section id="projects">
      <MarqueeComponent />
      <ProjectComponent />
      <MarqueeComponent />
    </section>
    <ContactComponent />
  </main>
  <FooterComponent />
</template>

<style scoped>
#hero {
  min-height: 100vh;
  max-height: 100vh;

  background: linear-gradient(
    to bottom, rgba(0, 0, 0, 0.3) 0%, rgba(0, 0, 0, 0.7) 75%, #000000 100%
    ), url("@/assets/img/Mountain.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  z-index: -10;
}

header {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: rgba(255, 255, 255, 0);
  transition: background-color 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  will-change: background-color;
  z-index: 100;
}

header.scrolled {
  background-color: rgba(255, 255, 255, 1);
}

main {
  position: relative;
  z-index: 1;
  margin-top: 100vh;
}

#about {
  background: #000000;
  padding: 2rem;
  text-align: center;
}

#projects {
  background-color: #FFFFFF;
}
</style>

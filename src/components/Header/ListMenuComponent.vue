<script>
  export default {
    methods: {
    scrollToAbout() {
      const about = document.getElementById("about");
      const top = about.getBoundingClientRect().top + window.scrollY - 91;
      window.scrollTo({top, behavior: 'smooth'});
    },
    scrollToProjects() {
      const projects = document.getElementById("projects");
      const top = projects.getBoundingClientRect().top + window.scrollY - 91;
      window.scrollTo({top, behavior: 'smooth'});
    },
    scrollToContact() {
      const contact = document.getElementById("contact");
      const top = contact.getBoundingClientRect().top + window.scrollY;
      window.scrollTo({top, behavior: 'smooth'});
    },
    }
  }
</script>

<template>
  <ul id="links">
      <li>
        <a 
          class="link-item" 
          href="#about"
          @click.prevent="scrollToAbout"
        >
        À propos
        </a>
      </li>
      <li>
        <a
        class="link-item"
        href="#projects"
        @click.prevent="scrollToProjects"
      >
      Projets
      </a>
      </li>
      <li>
        <a
        class="link-item"
        href="#contact"
        @click.prevent="scrollToContact"
        >
        Contact
        </a>
      </li>
    </ul>
</template>

<style scoped>

</style>
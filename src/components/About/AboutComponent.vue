<script>
  import IconsComponent from "@/components/Icons/IconsComponents.vue";

  export default {
    components: {
      IconsComponent
    }
  }
</script>

<template>
  <h2>Présentation</h2>
  <p>
    Passionné par les architectures back-end solides (Symfony) 
    et les interfaces réactives (Vue.js), j'allie performance et maintenabilité. 
    Je livre des applications optimisées et scalables grâce à Docker.
  </p>
  <div id="socials-links">
    <IconsComponent />
  </div>
</template>

<style scoped>
  h2 {
    font-size: 2rem;
    letter-spacing: 0.2rem;
    background: linear-gradient(rgba(255, 255, 255, 0.9), rgba(255, 255, 255, 0));
    -webkit-text-fill-color: transparent;
    background-clip: text;
    text-wrap: nowrap;
  }

  p {
    margin: 1rem auto;
    max-width: 768px;
    color: #FFFFFF;
  }
</style>
<script>
  export default {
    methods: {
      scrollToAbout() {
        const about = document.getElementById("about");
        const top = about.getBoundingClientRect().top + window.scrollY - 91;
        window.scrollTo({top, behavior: 'smooth'});
      }
    }
  }
</script>

<template>
  <div id="name">
    <h1>Kilian MINETTO</h1>
    <p>Développeur web</p>
    <button
    type="button"
    @click.prevent="scrollToAbout"
    >
    Me découvrir
    </button>
  </div>
  
</template>

<style scoped>
  #name {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
  }
  h1 {
    font-size: 6.5rem;
    letter-spacing: 0.8rem;
    background: linear-gradient(rgba(255, 255, 255, 0.9), rgba(255, 255, 255, 0));
    -webkit-text-fill-color: transparent;
    background-clip: text;
    text-wrap: nowrap;
  }
  p {
    color: rgba(255, 255, 255, 0.5);
    font-size: 1.25rem;
  }
  button {
    display: block;
    margin: 1.25rem auto;
    padding: 1.25rem;
    font-size: 1rem;
    color: #FFFFFF;
    background-color: #64a19d;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    letter-spacing: 0.3rem;
    transition: background-color 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    will-change: background-color;
  }
  button:hover {
    background-color: #548b87;
  }

  @media screen and (width <= 900px) {
    h1 {
      font-size: 1.6rem;
    }
    button {
      padding: 1rem;
    }
  }
  @media screen and (width < 350px) {
    h1 {
      font-size: 1.1rem;
    }
  }
</style>
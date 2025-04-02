<script>
  export default {
    
    methods: {
      buttonHovered() {
        const mobileMenu = document.getElementById('burger-wrapper');
        if (!mobileMenu.classList.contains('hovered')) {
          mobileMenu.classList.add('hovered');
        } else {
          mobileMenu.classList.remove('hovered')
        }
      },
      buttonClicked() {
        const mobileMenu = document.getElementById('burger-wrapper');
        if (!mobileMenu.classList.contains('clicked')) {
          mobileMenu.classList.add('clicked');
        } else {
          mobileMenu.classList.remove('clicked');
        }
      }
    },
    mounted() {
      const mobileMenu = document.getElementById('burger-wrapper');
      mobileMenu.addEventListener('mouseenter', this.buttonHovered);
      mobileMenu.addEventListener('mouseleave', this.buttonHovered);
    },
    beforeUnmount() {
      const mobileMenu = document.getElementById('burger-wrapper');
      mobileMenu.removeEventListener('mouseenter', this.buttonHovered);
      mobileMenu.removeEventListener('mouseleave', this.buttonHovered);
    }
  }
</script>

<template>
  <div
   id="burger-wrapper"
   @click.prevent="buttonClicked"
  >
    <span id="burger-line"></span>
  </div>
</template>

<style scoped>
  #burger-wrapper {
    position: relative;
    width: 50px;
    height: 50px;
    border: 1px solid #64a19d;
    border-radius: 5px;
    cursor: pointer;
  }
  #burger-line {
    position: relative;
    display: block;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 65%;
    height: 2px;
    background-color: #64a19d;
    margin: 0px 0 6px; /* Espace pour les autres lignes */
}

#burger-line::before {
  content: '';
  position: absolute;
  top: -10px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: inherit;
  transition: top 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  will-change: top;
}
#burger-line::after {
  content: '';
  position: absolute;
  top: 10px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: inherit;
  transition: top 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  will-change: top;
}

#burger-wrapper.hovered #burger-line::after {
  top: 8px;
}
#burger-wrapper.hovered #burger-line::before {
  top: -8px;
}
</style>
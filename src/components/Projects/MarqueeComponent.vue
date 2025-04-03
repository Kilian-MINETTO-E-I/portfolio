<script>
import { ref } from 'vue';
import { library } from '@fortawesome/fontawesome-svg-core';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { faHtml5, faCss3Alt, faJsSquare, faVuejs, faPhp, faSymfony, faDocker } from '@fortawesome/free-brands-svg-icons';
import { faDatabase } from '@fortawesome/free-solid-svg-icons';

library.add(faHtml5, faCss3Alt, faJsSquare, faVuejs, faPhp, faSymfony, faDocker, faDatabase);

export default {
  components: {
    'font-awesome-icon': FontAwesomeIcon
  },
  data() {
    return {
      icons: [
        ['fab', 'html5'],
        ['fab', 'css3-alt'],
        ['fab', 'js-square'],
        ['fab', 'vuejs'],
        ['fab', 'php'],
        ['fab', 'symfony'],
        ['fas', 'database'],
        ['fab', 'docker'],
      ],
      animationDuration: 20,
      isPaused: false,
      animationFrameId: null,
      scrollPosition: 0
    };
  },
  computed: {
    displayedIcons() {
      return [...this.icons, ...this.icons];
    },
    trackStyle() {
      return {
        transform: `translateX(${this.scrollPosition}px)`,
        transition: this.isPaused ? 'none' : 'transform 0.1s linear'
      };
    }
  },
  mounted() {
    this.startAnimation();
  },
  beforeUnmount() {
    this.stopAnimation();
  },
  methods: {
    getRandomSpeed() {
      return 0.5 + Math.random() * 1.5; // Entre 0.5 et 2
    },
    startAnimation() {
      const scrollSpeed = 1;

      const animate = () => {
        if (!this.isPaused) {
          this.scrollPosition -= this.getRandomSpeed();

          if (-this.scrollPosition >= this.$el.offsetWidth) {
            this.scrollPosition = 0;
          }
        }
        this.animationFrameId = requestAnimationFrame(animate);
      };
      animate();
    },
    stopAnimation() {
      if (this.animationFrameId) {
        cancelAnimationFrame(this.animationFrameId);
      }
    },
    pauseAnimation() {
      this.isPaused = true;
    },
    resumeAnimation() {
      this.isPaused = false;
    }
  }
};
</script>

<template>
  <div class="marquee-container" @mouseenter="pauseAnimation" @mouseleave="resumeAnimation">
    <div class="marquee-track" :style="trackStyle">
      <div v-for="(icon, index) in displayedIcons" :key="index" class="icon-item">
        <font-awesome-icon :icon="icon" class="tech-icon" />
      </div>
      <div v-for="(icon, index) in displayedIcons" :key="index" class="icon-item">
        <font-awesome-icon :icon="icon" class="tech-icon" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.marquee-container {
  width: 100%;
  overflow: hidden;
  white-space: nowrap;
  background-color: transparent;
  padding: 1rem 0;
  margin: 0 0 2rem;
  mask-image: linear-gradient(
    to right,
    transparent 0%,
    black 10%,
    black 90%,
    transparent 100%
  );
}
.marquee-track {
  display: inline-block;
  white-space: nowrap;
}
.icon-item {
  display: inline-block;
  margin: 0 2rem;
  vertical-align: middle;
}
.tech-icon {
  font-size: 3rem;
  color: #333333;
  transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.tech-icon:hover {
  transform: scale(1.2);
  color: #42b983; /* Couleur verte Vue.js par exemple */
}
@media (max-width: 768px) {
  .tech-icon {
    font-size: 2rem;
  }
  .icon-item {
    margin: 0 1rem;
  }
}
</style>
<script>
  import { ref } from 'vue'
  import { faArrowUp } from '@fortawesome/free-solid-svg-icons'
  import { library } from '@fortawesome/fontawesome-svg-core'

  library.add(faArrowUp)

  const currentYear = ref(new Date().getFullYear())

  export default {
    methods: {
      scrollToTop() {
         window.scrollTo({top: 0, behavior: 'smooth'});
      }
    }
  }
</script>

<template>
  <footer class="site-footer">
    <div class="footer-content">
      <div class="copyright">
        © Kilian MINETTO | Portfolio-{{ currentYear }}
      </div>
      
      <div class="footer-links">
        <a
          href="#"
          class="back-to-top"
          @click.prevent="scrollToTop"
        >
          <font-awesome-icon :icon="['fas', 'arrow-up']" />
          <span>Haut de page</span>
        </a>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background: linear-gradient(135deg, #35495e 0%, #2c3e50 100%);
  color: white;
  padding: 2rem 0;
  text-align: center;
  margin-top: auto; 
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  z-index: 500;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.copyright {
  font-size: 1rem;
  opacity: 0.8;
}

.footer-links {
  display: flex;
  gap: 1.5rem;
}

.back-to-top {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #42b983;
  text-decoration: none;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}

.back-to-top:hover {
  color: white;
  transform: translateY(-2px);
}

/* Effet au survol de l'icône */
.back-to-top svg {
  transition: transform 0.3s ease;
}

.back-to-top:hover svg {
  transform: translateY(-3px);
}

/* Responsive */
@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
  }
  
  .copyright {
    font-size: 0.9rem;
  }
}
</style>
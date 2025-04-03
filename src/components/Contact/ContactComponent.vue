<script>
import IconsComponent from "@/components/Icons/IconsComponents.vue";
import { faEnvelope, faPhone } from '@fortawesome/free-solid-svg-icons';
import { library } from '@fortawesome/fontawesome-svg-core';

library.add(faEnvelope, faPhone);

export default {
  components: {
    IconsComponent
  }
}

</script>

<template>
  <section id="contact" class="contact-section">
    <div class="contact-overlay"></div>
    <div class="contact-content">
      <h2>Contactez-moi</h2>
      <p class="contact-subtitle">Disponible pour de nouvelles opportunités</p>
      
      <div class="contact-info">
        <div class="contact-item">
          <font-awesome-icon :icon="['fas', 'envelope']" class="contact-icon" />
          <a href="mailto:kilian.minetto@protonmail.com" class="contact-link">kilian.minetto@protonmail.com</a>
        </div>
        
        <div class="contact-item">
          <font-awesome-icon :icon="['fas', 'phone']" class="contact-icon" />
          <a href="tel:+33659334127" class="contact-link">+33 6 59 33 41 27</a>
        </div>
      </div>

      <IconsComponent />
    </div>
  </section>
</template>

<style scoped>
  .contact-section {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(
    to bottom, rgba(0, 0, 0, 0.3) 0%, rgba(0, 0, 0, 0.7) 75%, #000000 100%
    ), url("@/assets/img/Forest.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    color: white;
    text-align: center;
    padding: 2rem;
  }

  .contact-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }

  .contact-content {
    position: relative;
    z-index: 1;
    max-width: 800px;
    width: 100%;
  }

  .contact-content h2 {
    font-size: 3rem;
    font-weight: 700;
    margin-bottom: 1rem;
    background: linear-gradient(90deg, #64a19d, #35495e);
    background-clip: linear-gradient(90deg, #64a19d, #35495e);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .contact-subtitle {
    font-size: 1.2rem;
    margin-bottom: 3rem;
    opacity: 0.9;
  }

  .contact-info {
    background-color: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border-radius: 15px;
    padding: 2rem;
    max-width: 500px;
    margin: 0 auto 2rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin: 1.5rem 0;
  }

  .contact-icon {
    font-size: 1.5rem;
    color: #42b983;
  }

  .contact-link {
    color: white;
    font-size: 1.2rem;
    text-decoration: none;
    transition: all 0.3s ease;
  }

  .contact-link:hover {
    color: #42b983;
    text-decoration: underline;
  }

  .social-links {
    display: flex;
    justify-content: center;
    gap: 2rem;
    margin-top: 2rem;
  }

  .social-links a {
    color: white;
    font-size: 2rem;
    transition: all 0.3s ease;
  }

  .social-links a:hover {
    color: #42b983;
    transform: translateY(-5px);
  }

  /* Responsive */
  @media (max-width: 768px) {
    .contact-content h2 {
      font-size: 2.5rem;
    }
    
    .contact-link {
      font-size: 1rem;
    }
  }
</style>
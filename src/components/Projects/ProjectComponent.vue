<script>
import { ref, computed } from 'vue' // Importez computed ici
import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faHtml5, faCss3Alt, faJsSquare, faVuejs, faPhp, faSymfony, faDocker, faGithub } from '@fortawesome/free-brands-svg-icons'
import { faDatabase } from '@fortawesome/free-solid-svg-icons'
import { faExternalLinkAlt } from '@fortawesome/free-solid-svg-icons'

library.add(faHtml5, faCss3Alt, faJsSquare, faVuejs, faPhp, faSymfony, faDocker, faDatabase, faGithub, faExternalLinkAlt)

export default {
  components: {
    'font-awesome-icon': FontAwesomeIcon
  },
  setup() {
    const projects = ref([
      {
        id: 1,
        title: "Oxipoxy",
        description: "E-commerce réalisé pour un client",
        tags: ["Symfony", "Responsive", "Stripe", "Database", "Docker"],
        github: null,
        live: "https://oxipoxy.fr",
        image: new URL('@/assets/img/oxipoxy.jpg', import.meta.url).href
      },
      {
        id: 2,
        title: "Solar System",
        description: "Projet personnel ThreeJs du système solaire",
        tags: ["Threejs", "Node.js"],
        github: "https://github.com/Kilian-MINETTO-E-I/SolarSystem",
        live: "https://solar-system-vert-eta.vercel.app/", // Pas de version en ligne
        image: new URL('@/assets/img/solarsystem.jpg', import.meta.url).href
      },
      {
        id: 3,
        title: "Movie App",
        description: "Projet NuxtJs, site de référencement de films",
        tags: ["Nuxtjs"],
        github: "https://github.com/KMinetto/InvoiceApp", // Code privé
        live: null,
        image: new URL('@/assets/img/movie-app.jpg', import.meta.url).href
      },
      {
        id: 4,
        title: "Soie Chic",
        description: "Projet E-commerce",
        tags: ["Symfony", "Stripe", "Database", "Docker"],
        github: null, // Code privé
        live: null,
        image: new URL('@/assets/img/soiechic.jpg', import.meta.url).href
      }
    ])
    const activeFilter = ref('all')

    const filteredProjects = computed(() => {
      if (activeFilter.value === 'all') return projects.value
      return projects.value.filter(p => p.tags.includes(activeFilter.value))
    })

    return {
      projects,
      activeFilter,
      filteredProjects
    }
  }
}
</script>

<template>
  <section class="projects-section">
    <h2 class="section-title">Mes Réalisations</h2>
    
    <div class="filter-buttons">
      <button 
        v-for="tag in ['all', 'Symfony', 'Threejs', 'Nuxtjs', 'Database', 'Docker']"
        :key="tag"
        @click="activeFilter = tag"
        :class="{ active: activeFilter === tag }"
      >
        {{ tag }}
      </button>
    </div>

    <div class="projects-grid">
      <div 
        v-for="project in filteredProjects" 
        :key="project.id" 
        class="project-card"
      >
        <div class="project-image">
          <img :src="project.image" :alt="project.title">
          <div class="project-links">
            <a 
              v-if="project.github" 
              :href="project.github" 
              target="_blank"
              class="github-link"
              aria-label="Code source sur GitHub"
            >
              <font-awesome-icon :icon="['fab', 'github']" />
            </a>
            <a 
              v-if="project.live" 
              :href="project.live" 
              target="_blank"
              class="live-link"
              aria-label="Voir le projet en ligne"
            >
              <font-awesome-icon :icon="['fas', 'external-link-alt']" />
            </a>
          </div>
        </div>
        
        <div class="project-info">
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
          <div class="project-tags">
            <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  padding: 4rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  text-align: center;
  margin-bottom: 3rem;
  font-size: 2.5rem;
  position: relative;
}

.section-title::after {
  content: "";
  display: block;
  width: 100px;
  height: 4px;
  background: linear-gradient(90deg, #42b983, #35495e);
  margin: 1rem auto 0;
}

.filter-buttons {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}

.filter-buttons button {
  padding: 0.5rem 1.5rem;
  border: 2px solid #42b983;
  background: transparent;
  color: #42b983;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-buttons button:hover,
.filter-buttons button.active {
  background: #42b983;
  color: white;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
}

.project-card {
  background: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.project-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
}

.project-image {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.05);
}

.project-links {
  position: absolute;
  bottom: 20px;
  right: 20px;
  display: flex;
  gap: 1rem;
}

.project-links a {
  width: 40px;
  height: 40px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #35495e;
  transition: all 0.3s ease;
}

.project-links a:hover {
  background: #42b983;
  color: white;
  transform: scale(1.1);
}

.project-info {
  padding: 1.5rem;
}

.project-info h3 {
  margin-bottom: 0.5rem;
  color: #35495e;
}

.project-info p {
  color: #666;
  margin-bottom: 1rem;
  line-height: 1.5;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.project-tags span {
  background: #f0f0f0;
  padding: 0.3rem 0.8rem;
  border-radius: 50px;
  font-size: 0.8rem;
  color: #555;
}

/* Indicateurs visuels pour les liens manquants */
.project-links a[disabled] {
  opacity: 0.5;
  pointer-events: none;
  background: rgba(255, 255, 255, 0.5);
}

/* Responsive */
@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>
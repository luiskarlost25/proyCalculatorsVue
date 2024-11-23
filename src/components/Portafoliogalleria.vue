<template>
    <div class="portfolio-gallery">
      <h2>Mi Portafolio</h2>
      <div class="grid">
        <div 
          v-for="(image, index) in paginatedImages" 
          :key="index" 
          class="grid-item">
          <img :src="image.src" :alt="image.alt" />
        </div>
      </div>
      <div class="controls">
        <button @click="prevPage" :disabled="currentPage === 1">⬅️ Anterior</button>
        <button @click="nextPage" :disabled="currentPage === totalPages">Siguiente ➡️</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'PortfolioGallery',
    data() {
      return {
        currentPage: 1,
        imagesPerPage: 6, // 2 filas x 3 columnas
        images: [
          { src: "https://via.placeholder.com/200", alt: "Imagen 1" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 2" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 3" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 4" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 5" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 6" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 7" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 8" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 9" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 10" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 11" },
          { src: "https://via.placeholder.com/200", alt: "Imagen 12" },
        ],
      };
    },
    computed: {
      totalPages() {
        return Math.ceil(this.images.length / this.imagesPerPage);
      },
      paginatedImages() {
        const start = (this.currentPage - 1) * this.imagesPerPage;
        return this.images.slice(start, start + this.imagesPerPage);
      },
    },
    methods: {
      nextPage() {
        if (this.currentPage < this.totalPages) {
          this.currentPage++;
        }
      },
      prevPage() {
        if (this.currentPage > 1) {
          this.currentPage--;
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .portfolio-gallery {
    text-align: center;
    margin: 20px auto;
  }
  
  h2 {
    color: #333;
  }
  
  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
    padding: 10px;
  }
  
  .grid-item img {
    width: 100%;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }
  
  .controls {
    margin-top: 10px;
  }
  
  button {
    background-color: #333;
    color: white;
    border: none;
    padding: 10px 15px;
    margin: 5px;
    cursor: pointer;
    border-radius: 5px;
  }
  
  button:disabled {
    background-color: #aaa;
    cursor: not-allowed;
  }
  </style>
  
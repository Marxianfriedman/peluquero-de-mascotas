<template>
  <section class="galeria">
    <h2 class="titulo-galeria">Nuestros Trabajos Artesanales</h2>
    <p class="descripcion-galeria">Transformación sin explotación capitalista</p>

    <div class="contenedor-galeria">
      <div v-for="(foto, index) in fotos" :key="index" class="item-galeria" @click="abrirLightbox(index)">
        <img :src="foto.thumbnail" :alt="'Peluquería canina - ' + foto.descripcion" loading="lazy">
        <div class="overlay">
          <span>{{ foto.descripcion }}</span>
        </div>
      </div>
    </div>

    <!-- Lightbox -->
    <div v-if="mostrarLightbox" class="lightbox" @click.self="cerrarLightbox">
      <button class="cerrar-lightbox" @click="cerrarLightbox">×</button>
      <img :src="fotos[indiceFotoActual].original" :alt="fotos[indiceFotoActual].descripcion">
      <p class="descripcion-lightbox">{{ fotos[indiceFotoActual].descripcion }}</p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'GaleriaDeFotos',
  data() {
    return {
      fotos: [
        {
          original: '/img/trabajo1.jpg',
          thumbnail: '/img/trabajo1-thumb.jpg',
          descripcion: 'Corte de raza para Golden Retriever'
        },
        {
          original: '/img/trabajo2.jpg',
          thumbnail: '/img/trabajo2-thumb.jpg',
          descripcion: 'Baño terapéutico para gato persa'
        },
        {
          original: '/img/trabajo3.jpg',
          thumbnail: '/img/trabajo3-thumb.jpg',
          descripcion: 'Muestra'
        },
        {
          original: '/img/trabajo4.jpg',
          thumbnail: '/img/trabajo4-thumb.jpg',
          descripcion: 'Muestra'
        },
        {
          original: '/img/trabajo5.jpg',
          thumbnail: '/img/trabajo5-thumb.jpg',
          descripcion: 'Muestra'
        },
        {
          original: '/img/trabajo6.jpg',
          thumbnail: '/img/trabajo6-thumb.jpg',
          descripcion: 'Muestra'
        },
        {
          original: '/img/trabajo7.jpg',
          thumbnail: '/img/trabajo7-thumb.jpg',
          descripcion: 'Muestra'
        },
        {
          original: '/img/trabajo8.jpg',
          thumbnail: '/img/trabajo8-thumb.jpg',
          descripcion: 'Muestra'
        },
        // Agrega más fotos...
      ],
      mostrarLightbox: false,
      indiceFotoActual: 0
    }
  },
  methods: {
    abrirLightbox(index) {
      this.indiceFotoActual = index;
      this.mostrarLightbox = true;
    },
    cerrarLightbox() {
      this.mostrarLightbox = false;
    }
  }
}
</script>

<style scoped>
.galeria {
  padding: 2rem 1rem;
  text-align: center;
}

.titulo-galeria {
  font-size: clamp(1.8rem, 4vw, 2.5rem);
  color: #333;
  margin-bottom: 0.5rem;
}

.descripcion-galeria {
  font-size: clamp(1rem, 2vw, 1.2rem);
  color: #666;
  margin-bottom: 2rem;
}

.contenedor-galeria {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1rem;
  padding: 0 1rem;
}

.item-galeria {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  aspect-ratio: 1 / 1;
  cursor: pointer;
}

.item-galeria:hover {
  transform: scale(1.03);
}

.item-galeria img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.8), transparent);
  color: white;
  padding: 1rem;
  text-align: left;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.item-galeria:hover .overlay {
  opacity: 1;
}

/* Lightbox */
.lightbox {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.9);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 2rem;
}

.lightbox img {
  max-width: 90%;
  max-height: 80vh;
  object-fit: contain;
}

.cerrar-lightbox {
  position: absolute;
  top: 2rem;
  right: 2rem;
  background: none;
  border: none;
  color: white;
  font-size: 2rem;
  cursor: pointer;
}

.descripcion-lightbox {
  color: white;
  margin-top: 1rem;
  text-align: center;
  max-width: 600px;
}

@media (max-width: 768px) {
  .contenedor-galeria {
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  }

  .lightbox img {
    max-width: 95%;
  }

  .cerrar-lightbox {
    top: 1rem;
    right: 1rem;
  }
}
</style>

<template>
  <div class="contenedor-principal">
    <header class="encabezado">
      <div class="contenido-de-encabezado">
        <h1 class="titulo">Harold el Peluquero de Mascotas</h1>
        <p class="subtitulo">Peluquero artesanal, nada de explotacion capitalista</p>

        <button class="boton">Contacta a Harold</button>
      </div>
    </header>

    <main class="caja-de-componentes">

    </main>

  </div>
</template>


<script>
export default {
  name: 'VistaPrincipal'
}
</script>

<style scoped>
.contenedor-principal {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.encabezado {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 2rem;
  background-color: rgba(0, 0, 0, 0.5);
  /* Overlay para mejor legibilidad */
  color: white;
  position: relative;
}

.contenido-de-encabezado {
  max-width: 800px;
  margin: 0 auto;
}

.titulo {
  font-size: clamp(2rem, 5vw, 3.5rem);
  margin-bottom: 1rem;
  font-weight: 700;
  line-height: 1.2;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.subtitulo {
  font-size: clamp(1.2rem, 3vw, 1.8rem);
  margin-bottom: 2rem;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.boton {
  background-color: #ff6b6b;
  color: white;
  border: none;
  padding: 1rem 2rem;
  font-size: 1.2rem;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: bold;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.boton:hover {
  background-color: #ff5252;
  transform: translateY(-3px);
  box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
}

.caja-de-componentes {
  padding: 2rem;
  background-color: rgba(56, 40, 40, 0.295);
}

/* Ajustes Responsivos */
@media (max-width: 768px) {
  .encabezado {
    padding: 1rem;
  }

  .boton {
    padding: 0.8rem 1.5rem;
    font-size: 1rem;
  }
}
</style>

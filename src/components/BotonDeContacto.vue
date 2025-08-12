<template>
  <button class="boton" @click="abrirModal">
    <slot>Contacta a Harold</slot>
  </button>

  <ModalContacto v-if="mostrarModal" @cerrar="cerrarModal" />
</template>

<script>
import ModalContacto from './ModalContacto.vue'

export default {
  name: 'BotonContacto',
  components: {
    ModalContacto
  },
  data() {
    return {
      mostrarModal: false
    }
  },
  methods: {
    abrirModal() {
      this.mostrarModal = true
    },
    cerrarModal() {
      this.mostrarModal = false
    }
  }
}
</script>

<style scoped>
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

@media (max-width: 768px) {
  .boton {
    padding: 0.8rem 1.5rem;
    font-size: 1rem;
  }
}
</style>

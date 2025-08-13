<template>
  <div class="modal-overlay" @click.self="cerrar">
    <div class="modal-contenido">
      <button class="cerrar-modal" @click="cerrar">×</button>

      <h2>Contacta a Harold</h2>
      <p>Reserva con Harold el complacera a tu mascota.</p>

      <form @submit.prevent="enviarFormulario" class="formulario-contacto">
        <div class="campo">
          <label for="nombre">Tu nombre:</label>
          <input id="nombre" v-model="formulario.nombre" type="text" required>
        </div>

        <div class="campo">
          <label for="nombre-mascota">Nombre(s) de tu(s) mascota(s):</label>
          <input id="nombre-mascota" v-model="formulario.nombreMascota" type="text">
        </div>

        <div class="campo">
          <label for="tipo-mascota">Tipo de mascota:</label>
          <select id="tipo-mascota" v-model="formulario.tipoMascota" required>
            <option value="perro">Perro(s)</option>
            <option value="gato">Gato(s)</option>
            <option value="otro">Otra(s) mascota(s)</option>
          </select>
        </div>

        <div class="campo">
          <label for="raza">Raza:</label>
          <input id="raza" v-model="formulario.raza" type="text">
        </div>

        <div class="campo">
          <label for="edad">Edad aproximada:</label>
          <input id="edad" v-model="formulario.edad" type="text" placeholder="Ej: 2 años">
        </div>

        <div class="campo">
          <label for="servicio">Servicio requerido:</label>
          <select id="servicio" v-model="formulario.servicio" required>
            <option value="baño">Baño completo</option>
            <option value="corte">Corte de pelo</option>
            <option value="completo">Baño + Corte</option>
            <option value="otro">Otro servicio</option>
          </select>
        </div>

        <div class="campo">
          <label for="mensaje">Detalles adicionales:</label>
          <textarea id="mensaje" v-model="formulario.mensaje" rows="3"></textarea>
        </div>

        <button type="submit" class="boton-enviar">
          Enviar a WhatsApp
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalContacto',
  emits: ['cerrar'],
  data() {
    return {
      formulario: {
        nombre: '',
        nombreMascota: '',
        tipoMascota: 'perro',
        raza: '',
        edad: '',
        servicio: 'baño',
        mensaje: ''
      }
    }
  },
  methods: {
    cerrar() {
      this.$emit('cerrar')
    },
    enviarFormulario() {
      const mensajeWhatsApp = this.generarMensajeWhatsApp()
      const numeroHarold = '573118062774'

      window.open(
        `https://wa.me/${numeroHarold}?text=${encodeURIComponent(mensajeWhatsApp)}`,
        '_blank'
      )

      this.cerrar()
    },
    generarMensajeWhatsApp() {
      return `¡Hola Harold! Quiero reservar una cita:

*Mi nombre es:* ${this.formulario.nombre}

*Sobre mi mascota:*
- Nombre: ${this.formulario.nombreMascota || 'sin nombre'}
- Tipo: ${this.formulario.tipoMascota}
- Raza: ${this.formulario.raza || 'No especificada'}
- Edad: ${this.formulario.edad || 'No especificada'}

*Servicio:* ${this.formalizarServicio(this.formulario.servicio)}

*Detalles adicionales:*
${this.formulario.mensaje || 'Ninguno'}

¡Gracias!`
    },
    formalizarServicio(servicio) {
      const servicios = {
        'baño': 'Baño completo',
        'corte': 'Corte de pelo',
        'completo': 'Baño + Corte',
        'otro': 'Otro servicio'
      }
      return servicios[servicio] || servicio
    }
  }
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-contenido {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  width: 90%;
  max-width: 500px;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
}

.cerrar-modal {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
}

h2 {
  color: #333;
  margin-bottom: 0.5rem;
}

p {
  color: #666;
  margin-bottom: 1.5rem;
}

.formulario-contacto {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-weight: 500;
  color: #444;
}

input,
select,
textarea {
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-family: inherit;
}

textarea {
  resize: vertical;
}

.boton-enviar {
  background-color: #25D366;
  color: white;
  border: none;
  padding: 1rem;
  border-radius: 4px;
  font-weight: bold;
  cursor: pointer;
  margin-top: 1rem;
  transition: background-color 0.3s;
}

.boton-enviar:hover {
  background-color: #128C7E;
}

@media (max-width: 768px) {
  .modal-contenido {
    padding: 1.5rem;
    width: 95%;
  }
}
</style>

<template>
  <footer class="footer">
    <div class="contenedor-footer">
      <!-- Sección de información -->
      <div class="seccion-info">
        <h3 class="titulo-footer">Harold el Peluquero de Mascotas</h3>
        <p class="eslogan">Peluquería artesanal libre de explotación capitalista</p>

        <div class="info-contacto">
          <p>✂️ Trabajo con amor y cuidado animal</p>
          <p>📍 Ubicación: Bajo el puente de la 80 con Cali</p>
          <p>🕒 Horario: Lunes a Sábado 9am - 6pm</p>
        </div>
      </div>

      <!-- Sección de contacto rápido -->
      <div class="seccion-contacto">
        <h4>Contacto directo</h4>
        <BotonDeContacto version="footer">
          <template v-slot:default>
            📞 WhatsApp directo
          </template>
        </BotonDeContacto>

        <div class="redes-sociales">
          <a href="#" class="red-social" aria-label="Instagram">
            <span class="icono">📸</span> @HaroldPeluquero
          </a>
          <a href="#" class="red-social" aria-label="Facebook">
            <span class="icono">👍</span> Harold Peluquería Canina
          </a>
        </div>
      </div>

      <!-- Mensaje final -->
      <div class="mensaje-final">
        <p>¡Los animales merecen cuidado ético sin explotación capitalista!</p>
        <p class="copyright">© {{ añoActual }} Harold - Todos los derechos reservados</p>
      </div>
    </div>
  </footer>
</template>

<script>
import BotonDeContacto from './BotonDeContacto.vue';

export default {
  name: 'PieDePagina',
  components: {
    BotonDeContacto
  },
  data() {
    return {
      añoActual: new Date().getFullYear()
    }
  }
}
</script>

<style scoped>
.footer {
  background-color: #2c3e50;
  color: #ecf0f1;
  padding: 2rem 1rem;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.contenedor-footer {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
}

.titulo-footer {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: #ff6b6b;
}

.eslogan {
  font-style: italic;
  margin-bottom: 1rem;
  color: #bdc3c7;
}

.info-contacto p {
  margin: 0.5rem 0;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.seccion-contacto {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.seccion-contacto h4 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
}

.redes-sociales {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.red-social {
  color: #ecf0f1;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: color 0.3s;
}

.red-social:hover {
  color: #ff6b6b;
}

.icono {
  font-size: 1.2rem;
}

.mensaje-final {
  margin-top: 2rem;
  text-align: center;
  border-top: 1px solid #34495e;
  padding-top: 1rem;
}

.mensaje-final p:first-child {
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.copyright {
  font-size: 0.9rem;
  color: #bdc3c7;
}

/* Versión responsiva */
@media (min-width: 768px) {
  .contenedor-footer {
    grid-template-columns: 1fr 1fr;
  }

  .mensaje-final {
    grid-column: span 2;
  }
}

@media (min-width: 1024px) {
  .contenedor-footer {
    grid-template-columns: 2fr 1fr;
  }
}
</style>

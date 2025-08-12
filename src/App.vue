<template>
  <div class="contenedor">
    <VistaPrincipal />
  </div>
</template>

<script>
import VistaPrincipal from './views/VistaPrincipal.vue';

export default {
  components: {
    VistaPrincipal
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  height: 100%;
  width: 100%;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.contenedor {
  min-height: 100vh;
  width: 100%;
  background: url(/public/fondo2.jpg) no-repeat center center fixed;
  background-size: cover;
  display: flex;
  flex-direction: column;
}
</style>

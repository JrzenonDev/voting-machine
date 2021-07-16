<template>
  <div id="app">
    <div class="urna">
      <Tela />
      <Teclado />
    </div>
  </div>
</template>

<script>
import Tela from '@/components/Tela.vue';
import Teclado from '@/components/Teclado.vue';

import '@/css/globals.css';

export default {
  name: 'App',
  components: {
    Tela,
    Teclado
  }
}
</script>

<style scoped>
  #app {
    background-color: var(--background-color);
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .urna {
    width: 1000px;
    height: 500px;
    background-color: var(--ballot-box-background-color);
    padding: 30px;
    border-radius: 5px;
    display: flex;
  }
</style>
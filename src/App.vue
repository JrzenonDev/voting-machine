<template>
  <div id="app">
    <div class="urna">
      <Tela
        :tela ="tela"
        :numeroVoto="numeroVoto"
        :quantidadeNumeros="quantidadeNumeros"
        :candidato="candidato"
      />
      <Teclado
        :adicionarNumero="adicionarNumero"
      />
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
  },
  methods: {
    adicionarNumero(numero) {
      // verify limit voted number
      if (this.numeroVoto.length == this.quantidadeNumeros) {
        return false;
      }
      // add selected number
      this.numeroVoto += ''+numero;

      this.verificarCandidato();
    },
    verificarCandidato() {
      // voted imcomplete
      if (this.numeroVoto.length < this.quantidadeNumeros) {
        return false;
      }

      // check if the candidate exists
      if (this.candidatos[this.tela][this.numeroVoto]) {
        this.candidato = this.candidatos[this.tela][this.numeroVoto];
        return true;
      }

      // vote null
      this.candidato = {
       nome: 'Voto nulo',
       partido: 'Voto nulo',
       imagem: ''
      }
    }
  },
  data() {
    return {
      tela: 'prefeito',
      numeroVoto: '',
      quantidadeNumeros: 2,
      candidato: {},
      candidatos: {
        "prefeito":{
          "01":{
            "nome": "Ash",
            "partido": "Pokemon",
            "imagem": "/assets/images/ash.png"
          },
          "08":{
            "nome": "Vegeta",
            "partido": "Dragon Ball",
            "imagem": "/assets/images/vegeta.png"
          }
        },
        "vereador":{
          "01234":{
            "nome": "Pikachu",
            "partido": "Pokemon",
            "imagem": "/assets/images/pikachu.png"
          },
          "08001":{
            "nome": "Goku",
            "partido": "Dragon Ball",
            "imagem": "/assets/images/goku.png"
          }
        }
      }
    }
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
    justify-content: space-between;
  }
</style>
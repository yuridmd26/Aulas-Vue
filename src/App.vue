<template>
  <div id="app">
    <caixas :caixinhas="caixinhas"/>
    <ferramentas :caixinhas="caixinhas" @alteraCor="alteraCor($event)" @alterouTexto="alteraTexto($event)"/>
  </div>
</template>

<script>
import Caixas from "./components/Caixas.vue"
import Ferramentas from "./components/Ferramentas.vue"
export default {
  name: 'App',
  components: {
    Caixas, Ferramentas
  }, data: function() {
    return {
      caixinhas: [{
        Titulo: "1", 
        cor: "background: red"
      }, {
        Titulo: "2",
        cor: "background: blue"
      }, {
        Titulo: "3",
        cor: "background: orange"
      }]
    }
  }, methods: {
    alteraCor: function(event) {
      this.caixinhas[event.caixa].cor = event.cor
    }, alteraTexto: function(event) {
    console.log(event)
    this.caixinhas[event.caixa].Titulo = event.titulo
  }
  }
}
</script>

<style>

</style>
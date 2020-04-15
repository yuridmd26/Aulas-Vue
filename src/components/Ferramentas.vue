<template>
<div id="ferramentas">
  <select v-model="corSel">
      <option value="" selected disabled> Selecione uma caixa</option>
      <option v-for="(caixa, index) in caixinhas" :key="index" :value="index">
        {{caixa.Titulo}}
      </option>
  </select>

  <div id="paleta">
      <div class="cor" :style="cor" v-for="(cor, index) in cores" :key="index" @click="alteraCor(cor)">
      </div>
  </div>
    <input type="text" placeholder="Digite o nome da caixa" v-model="titulo">
    <button @click="alterarTexto">OK</button>
</div>


</template>

<script>

export default {
    name: "Ferramentas",
    props: ['caixinhas'],
    data: function() {
        return {
            cores: ['background: brown', 'background: white', 'background: green'],
            corSel: '',
            titulo: ''
        }
    }, methods: {
        alteraCor: function(cor) {
            this.$emit('alteraCor', {
                cor: cor,
                caixa: this.corSel
            })
        }, alterarTexto: function() {
        this.$emit('alterouTexto', {
            titulo: this.titulo,
            caixa: this.corSel
        })
    }
    }
}
</script>

<style>
  #ferramentas {
      width: 380px;
      height: 150px;
      border: 1px solid #FFF;
      margin: 5px auto 0px auto;
      padding: 10px;
  }
  #ferramentas select {
      width: 200px;  
      margin-bottom: 5px;   
  }

  #paleta {
      width: 380px;
      height: 150px;
      display: flex;
      
  }

  .cor {
      width: 60px;
      height: 60px;
      border: 1px solid #FFF;
      margin-right: 5px;
  }
</style>
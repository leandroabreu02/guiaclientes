<template>
  <div :class ="{'cliente': !isPremium, 'cliente-premium': isPremium}">
    <h4>Nome: {{ cliente.nome }}</h4>
    <hr>
    <p>E-mail: {{ cliente.email | processarEmail }}</p>
    <p v-if="showIdade === true">Idade: {{ cliente.idade }}</p>
    <p v-else>O usuário escondeu a idade</p>
    <button @click="mudarCor($event)">Mudar cor</button>
    <button @click="emitirEventoDelete">Deletar</button>
    <h4>Id especial: {{ idEspecial }}</h4>
    <!-- <input type="text" :value="nome">     -->
    <!-- os dois pontos servem para colocar uma variável dentro de um atribulo html -->
    <!-- data binding, ligando um dado em um campo de formulário -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPremium: false 
    }
  },
  props: {
    cliente: Object,
    showIdade: Boolean
  },
  methods: {
    mudarCor: function($event) {
      console.log($event);
      this.isPremium = !this.isPremium;
    },
    emitirEventoDelete: function() {
      console.log('Emitindo');
      this.$emit("meDelete", {idDoCliente: this.cliente.id, curso: "Formação Node.js", emPromocao: true, componen: this});
    },
    testar: function() {
      console.log("Testando para valer");
      alert("Isso é um alert!");
    }
  },
  filters: {
    processarEmail: function(value) {
      return "GUIADOPROGRAMADOR." + value.toUpperCase();
    }
  },
  computed: {
    idEspecial: function() {
      return (this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase();
    }
  }
}
</script>

<style scoped>  
/* esse scoped significa que esse estilo só vai ser aplicado nesse componente */
  .cliente {
    background-color: #ECE5E3;
    max-width: 600px;
    height: 180px;
    padding: 1%;
    margin-top: 2%;
  }

  .cliente-premium {
    background-color: black;
    color: yellow;
    max-width: 600px;
    height: 180px;
    padding: 1%;
    margin-top: 2%;
  }
</style>
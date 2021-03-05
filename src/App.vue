<template>
  <div id="app">

    <div class="buttons">
      <button class="button is-primary">Primary</button>
      <button class="button is-link">Link</button>
    </div>

    <h3>Cadastro: </h3>
    <small id="nomeErro" v-show="deuErro">O nome é inválido, digite novamente</small> <br>
    <input type="text" placeholder="nome" v-model="nomeField"> <br>
    <input type="email" placeholder="email" v-model="emailField"> <br>
    <input type="number" placeholder="idade" v-model="idadeField"> <br>
    <button @click="cadastrarUsuario">Cadastrar</button>
    <hr>
    <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
      <h4>{{ index + 1 }}</h4>
      <Cliente :cliente="cliente" @meDelete="deleterUsuario($event)"/>
    </div>
  </div>
</template>

<script>
import _ from 'lodash';
import Cliente from './components/Cliente';
// import Produto from './components/Produto';

export default {
  name: 'App',
  data() {
    return {
      deuErro: false,
      nomeField: "",
      emailField: "",
      idadeField: 0,
      clientes: [
        {
          id: 1,
          nome: "Leandro Cardoso",
          email: "djleandro.cardoso@gmail.com",
          idade: 18
        },
        {
          id: 2,
          nome: "Leandro Abreu",
          email: "leandroabreu@gmail.com",
          idade: 16
        }
      ]
    }
  },
  components: {
    Cliente,
    // Produto
  },
  methods: {
    cadastrarUsuario: function() {
      if(this.nomeField == "" || this.nomeField == " " || this.nomeField.lengh < 3) {
        this.deuErro = true;
      }else {
        this.clientes.push({ nome: this.nomeField, email: this.emailField, idade: this.idadeField, id: Date.now() })
        this.nomeField = "";
        this.emailField = "";
        this.idadeField = 0;
        this.deuErro = false;
      }
    },
    deleterUsuario: function($event) {
      var id = $event.idDoCliente;
      var novoArray = this.clientes.filter(cliente => cliente.id != id);
      this.clientes = novoArray;
    }
  },
  computed: {
    orderClientes: function() {
      return _.orderBy(this.clientes, ['nome', ['asc']])
    }
  }
}
</script>

<style>
  #nomeErro {
    color: red;
  }
</style>

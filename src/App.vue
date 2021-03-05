<template>
  <div id="app">
    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h4>{{ index + 1 }}</h4>
      <Cliente :cliente="cliente"/>
      <hr>
      <h4>Edição: </h4>
      <input type="text" v-model="cliente.nome">
      <input type="text" v-model="cliente.email">
    </div>
  </div>
</template>

<script>
import Cliente from './components/Cliente';
// import Produto from './components/Produto';

export default {
  name: 'App',
  data() {
    return {
      nomeDoLeandro: "Leandro Cardoso",
      clienteLeandro: {
        nome: "Leandro C",
        email: "djleandro.cardoso@gmail.com",
        idade: 18
      },
      clientes: [
        {
          id: 1,
          nome: "Pessoa1",
          email: "p1@gmail.com",
          idade: 20
        },
        {
          id: 2,
          nome: "Pessoa2",
          email: "p2@gmail.com",
          idade: 30
        },
        {
          id: 3,
          nome: "Pessoa3",
          email: "p3@gmail.com",
          idade: 40
        },
        {
          id: 4,
          nome: "Pessoa4",
          email: "p4@gmail.com",
          idade: 50
        },
        {
          id: 5,
          nome: "Pessoa5",
          email: "p5@gmail.com",
          idade: 60
        }
      ]
    }
  },
  components: {
    Cliente,
    // Produto
  }
}
</script>

<style>

</style>

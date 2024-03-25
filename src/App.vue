<script setup>
import { reactive, ref } from 'vue'

const titulo = ref('Meu VueJS!!')
const mostrarResultado = ref(false)

const produto = reactive({
  nome: '',
  preco: 0,
  estoque: 0,
  categorias: []
})

function formatarPreco(preco) {
  return `R$ ${preco.toFixed(2).replace('.', ',')}`
}
</script>

<template>
  <h1>{{ titulo }}</h1>
  <div class="container">
    <div class="formulario">
      <h2>Formulario</h2>
      <input type="text" v-model="titulo" />
      <hr />
      <div class="row">
        <label for="">Nome:</label>
        <input type="text" v-model="produto.nome" />
      </div>
      <div class="row">
        <label for="">Preço:</label>
        <input type="number" v-model="produto.preco" />
      </div>
      <div class="row">
        <label for="">Estoque:</label>
        <input type="number" v-model="produto.estoque" />
      </div>
      <div class="row">
        <label for="">Categoria:</label>
        <input type="text" v-model="produto.categorias" />
      </div>
      <button @click="mostrarResultado = !mostrarResultado">Mostrar Resultado</button>
    </div>
    <Transition>
      <div v-if="mostrarResultado" class="resultado">
        <h2>Resultado</h2>
        <h3>Dados do produto</h3>
        <p>Nome: {{ produto.nome }}</p>
        <p>Preço: {{ formatarPreco(produto.preco) }}</p>
        <p>Estoque: {{ produto.estoque }}</p>
        <p>Categorias: {{ produto.categorias }}</p>
        <p>{{ mostrarResultado }}</p>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  column-gap: 2rem;
  margin-top: 1rem;
}

.formulario,
.resultado {
  min-height: 80vh;
  width: 80vh;
  border-radius: 10px;
  padding: 10px;
}
.formulario {
  background-color: rgb(92, 184, 184);
}
.resultado {
  background-color: rgb(172, 127, 72);
}
.v-enter-active,
.v-leave-active{
  transition: opacity 1s ease;
}

.v.enter-from {
  opacity: 0;
}
.v-enter-to {
  opacity: 1;
}
</style>

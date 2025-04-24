<script setup>
import { ref, computed } from 'vue'

import pé from './componentes/footer.vue'

const Livros = ref([
  { id: 1, titulo: 'Nog Ognia', autor: 'Eric-Emanuel Schimitt', preco: 0 },
  { id: 2, titulo: 'O Alquimista', autor: 'Paulo Coelho', preco: 69.9 },
  { id: 3, titulo: 'O Hobbit', autor: 'J. R. R. Tolkien', preco: 69.9 },
  { id: 4, titulo: 'Pegasus e o fogo do Olimpo', autor: 'Kate O Hearn', preco: 41.0 },
  {
    id: 5,
    titulo: 'O ratinho, o morango vermelho maduro e o grande urso esfomeado',
    autor: 'Audrey Wood',
    preco: 64.9,
  },
  {
    id: 6,
    titulo: 'Pai Rico, pai Pobre: Edição de 20 Anos Atualizada e Ampliada',
    autor: 'Kiyosaki Robert T',
    preco: 54.69,
  },
  { id: 7, titulo: 'O homem mais rico da Babilônia', autor: 'George S Clason', preco: 34.9 },
  { id: 8, titulo: 'Nunca deixe de tentar', autor: 'Michael Jordan', preco: 39.9 },
])
const Carrinho = ref([])
function AdicionarCarrinho() {
  Carrinho.value.push(Livros.value[0])
}
function RemoverCarrinho() {
  Carrinho.value.pop()
}
// Soma automática baseada no conteúdo do carrinho
const valorTotal = computed(() => {
  return Carrinho.value.reduce((total, livro) => total + livro.preco, 0)
})

const totalCompras = computed(() => {
  return {
    produtos: valorTotal.value,
    frete: 'Grátis',
    total: valorTotal.value,
  }
})
</script>

<template>
  <div class="carrinho" @click="Button">
    <div class="adicionar">
    <h1>Carrinho</h1>
    <ul>
      <li><p>Título</p></li>
      <li><p>Quantidade</p></li>
      <li><p>Subtotal</p></li>
    </ul>
    </div>
    <button class="voltar">Voltar para loja</button>
     <p><input type="text"> <button>Inserir Cupom</button></p>
  </div>
  <div class="footer">
    <pé />
  </div>
</template>

<style scoped></style>

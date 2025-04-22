<script setup>

const Livros = ref([
  { id: 1, titulo: 'Nog Ognia', autor: 'Eric-Emanuel Schimitt', preco: 0},
  { id: 2, titulo: 'O Alquimista', autor: 'Paulo Coelho', preco: 69.90 },
  { id: 3, titulo: 'O Hobbit', autor: 'J. R. R. Tolkien', preco: 69.90 },
  { id: 4, titulo: 'Pegasus e o fogo do Olimpo', autor: 'Kate O Hearn', preco: 41.00},
  { id: 5, titulo: 'O ratinho, o morango vermelho maduro e o grande urso esfomeado', autor: 'Audrey Wood', preco: 64.90},
  { id: 6, titulo: 'Pai Rico, pai Pobre: Edição de 20 Anos Atualizada e Ampliada', autor: 'Kiyosaki Robert T', preco: 54.69},
  { id: 7, titulo: 'O homem mais rico da Babilônia', autor: 'George S Clason' preco: 34.90},
  { id: 8, titulo: 'Nunca deixe de tentar', autor: 'Michael Jordan', preco: 39.90},
  
]);
const Carrinho = ref([]);
function AdicionarCarrinho() {
     Carrinho.value.push(Livros.value[0]);
}
function RemoverCarrinho() {
     Carrinho.value.pop();
}

</script>

<template>

</template>

<style scoped>

</style>

<script setup>

const Livros = ref([
  { id: 1, titulo: '', autor: '', preco: 0},
  { id: 2, titulo: '', autor: '', preco: 0 },
  { id: 3, titulo: '', autor: '', preco: 0 },
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

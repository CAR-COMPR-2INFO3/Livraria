<script setup>
import footerComp from './componentes/footer.vue'
import { ref, computed } from 'vue'

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
  <carrinho/>
    <div class="carrinho">
      <div class="adicionar">
        <h1>Carrinho</h1>
        <ul>
          <li>
            <p>Título</p>
          </li>
          <li>
            <p>Quantidade</p>
          </li>
          <li>
            <p>Subtotal</p>
          </li>
        </ul>
      </div>
      <button class="voltar">Voltar para loja</button>
      <p><input type="text" placeholder="Código do Cupom"><button class="verde">Inserir Cupom</button></p>
      <div class="total">
        <h2>Total da Compra</h2>
        <ul>
          <li>
            <p>Produtos:<span> R${{ totalCompras.produtos }}</span></p>
            <hr>
          </li>
          <li>
            <p>Frete: <span> {{ totalCompras.frete }}</span></p>
            <hr>
          </li>
          <li>
            <p>Total: <span> R${{ totalCompras.total }}  </span></p>
          </li>
        </ul>
        <button class="verde">Ir para o pagamento</button>
      </div>
    </div>
    <div class="footer">
      <footer-comp />
    </div>
</template>

<style scoped>
.carrinho {
  padding: 4vw;
}

.adicionar h1 {
  color: #27AE60;
  font-size: 2vw;
  font-weight: bold;
  margin: 0 0 3vw 0;
}

.adicionar ul {
  display: flex;
  justify-content: space-between;
  border-bottom: #27AE60 solid 2px;
  padding: 0 0 1vw 0;
}
input {
  padding: 0.9vw 1.9vw 0.9vw 1.9vw;
  border-radius: 0.2vw;
  margin: 0 0.6vw 0 0;
}
.voltar {
  padding: 0.9vw 1.9vw 0.9vw 1.9vw;
  border-radius: 0.2vw;
  background-color: white;
  border-color: gray;
  margin: 0 0 4vw 0;
}
.total {
  display: flex;
  flex-direction: column;
  margin: 0 0 0 60vw;
  padding: 2vw;
  border: 1px solid black;
  border-radius: 7px;
}
.total h2 {
  margin: 0 0 2vw 0;
  font-size: 1.3vw;
  font-weight: bold;
}
.total p {
  margin: 0 0 2vw 0;
}


</style>

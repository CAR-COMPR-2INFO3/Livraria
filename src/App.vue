<script setup>
import { ref, computed } from 'vue'

import footerComp from './components/footer.vue'

const Livros = ref([
  { id: 1, titulo: 'Nog Ognia', autor: 'Eric-Emanuel Schimitt', preco: 66.50 },
  { id: 2, titulo: 'O Alquimista', autor: 'Paulo Coelho', preco: 69.90 },
  { id: 3, titulo: 'O Hobbit', autor: 'J. R. R. Tolkien', preco: 69.90 },
  { id: 4, titulo: 'Pegasus e o fogo do Olimpo', autor: 'Kate O Hearn', preco: 41.00 },
  { id: 5, titulo: 'O ratinho, o morango vermelho maduro e o grande urso esfomeado', autor: 'Audrey Wood', preco: 64.90 },
  { id: 6, titulo: 'Pai Rico, pai Pobre: Edição de 20 Anos Atualizada e Ampliada', autor: 'Kiyosaki Robert T', preco: 54.69 },
  { id: 7, titulo: 'O homem mais rico da Babilônia', autor: 'George S Clason', preco: 34.90 },
  { id: 8, titulo: 'Nunca deixe de tentar', autor: 'Michael Jordan', preco: 39.90 }

]);


const carrinhoAparecer = ref(false);
const botao = computed(() =>
  carrinhoAparecer.value ? 'Esconder' : 'Mostrar',
);



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

  <header>


    <nav>
      <div class="logo">
        <a href="App.vue"><img src="/public/img/logo.png" alt="logo"></a>
      </div>

      <div class="barra">
        <form action="#" method="get">
          <p>
            <input type="text" id="barra-pesquisa" placeholder="Pesquisar">
            <span class="mdi mdi-magnify"></span>
          </p>
        </form>
      </div>
      <div class="paginas">
        <ul>
          <li>
            <a href="#">Termos</a>
          </li>
          <li>
            <a href="#">Equipe</a>
          </li>
          <li>
            <a href="#">Envio</a>
          </li>
          <li>
            <a href="#">Devoluções</a>
          </li>
        </ul>
      </div>
      <div class="icones">
        <nav>
          <ul>
            <li>
              <p>
                <button @click="carrinhoAparecer = !carrinhoAparecer">
                  <span class="invisible">{{ botao }}</span>
                  <span class="fi fi-sr-shopping-cart"></span>
                </button>
              </p>
            </li>
            <li>
              <p>|</p>
            </li>
            <li>
              <p>
                <button>
                  <span class="fi fi-sr-heart"></span>
                </button>
              </p>
            </li>
            <li>
              <p>|</p>
            </li>
            <li>
              <p>
                <button>
                  <span class="fi fi-sr-user"></span>
                </button>
              </p>
            </li>
          </ul>
        </nav>
      </div>
    </nav>
    <hr />

  </header>


  <main>

    <div v-if="!carrinhoAparecer">
      <section class="autor">Autor de Abril</section>
    </div>
    <div v-if="carrinhoAparecer">
      <carrinho />

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
              <p>Total: <span> R${{ totalCompras.total }} </span></p>
            </li>
          </ul>
          <button class="verde">Ir para o pagamento</button>
        </div>
      </div>
    </div>
    <div class="footer">
      <footer-comp />
    </div>
  </main>


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

/*========================= HEADER =========================*/

/* GERAL */

header nav {
  margin: 1.5%;
  padding: 0 3vw 0 3vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* LOGO */

header nav div.logo {
  margin: 7px 0 0 0;
}


/* BARRA */

header nav div.barra form p {
  background-color: #F1F1F1;
  justify-content: space-between;
  padding: 7px 1vw 0.5vw 1vw;
  margin: 0 0 0 0;
}

header nav div.barra form p input {
  border: none;
  background: #F1F1F1;
  color: #B8B8B8;
  font-size: 1rem;
  padding: 0 1vw 0 0;
  outline: none;
}

/* PAGINAS */

header nav div.paginas ul {
  display: flex;
}

header nav div.paginas ul li a {
  color: #7B7881;
  padding: 0 4vw 0 0;
}


/* ICONES */

header nav div.icones nav ul {
  display: flex;

}

header nav div.icones nav ul li {
  padding: 0 20px 0 0;
  color: green;
}

header nav div.icones nav ul li p button {
  color: green;
  border: none;
  background: none;
  font-size: 18px;
}

hr {
  color: #27AE60;
}

.invisible {
  display: none;
}
</style>

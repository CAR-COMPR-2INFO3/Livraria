<script setup>
import { ref, computed } from 'vue'

import footerComp from './components/footer.vue'

const Livros = ref([
  { id: 1, titulo: 'Noc Ognia', autor: 'Eric-Emanuel Schimitt', preco: 66.50, img: '/img/livros/noc-ognia.jpg' },
  { id: 2, titulo: 'O Alquimista', autor: 'Paulo Coelho', preco: 69.90, img: '/img/livros/paulo_coelho.jpg' },
  { id: 3, titulo: 'O Hobbit', autor: 'J. R. R. Tolkien', preco: 69.90, img: '/img/livros/o_hobbit.jpg' },
  { id: 4, titulo: 'Pegasus e o fogo do Olimpo', autor: 'Kate O Hearn', preco: 41.00, img: '/img/livros/pegasus-e-o-fogo-do-olimpo.png' },
  { id: 5, titulo: 'O ratinho, o morango vermelho maduro e o grande urso esfomeado', autor: 'Audrey Wood', preco: 64.90, img: '/img/livros/o-ratinho-o-morango-vermelho-maduro-e-o-grande-urso-esfomeado.jpg' },
  { id: 6, titulo: 'Pai Rico, pai Pobre: Edição de 20 Anos Atualizada e Ampliada', autor: 'Kiyosaki Robert T', preco: 54.69, img: '/img/livros/pai-rico-pai-pobre.jpg' },
  { id: 7, titulo: 'O homem mais rico da Babilônia', autor: 'George S Clason', preco: 34.90, img: '/img/livros/o-homem-mais-rico-da-babilonia.jpg' },
  { id: 8, titulo: 'Nunca deixe de tentar', autor: 'Michael Jordan', preco: 39.90, img: '/img/livros/nunca-deixe-de-tentar.jpg' }

]);

const carrinhoAparecer = ref(false);
const botao = computed(() => (carrinhoAparecer.value ? 'Esconder' : 'Mostrar'));

const Carrinho = ref([])
function AdicionarCarrinho(livro) {
  Carrinho.value.push(livro);
}
function RemoverCarrinho() {
  Carrinho.value.pop();
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
});
let quantidade = ref(0);
function contadorSom(quantidadeq){
quantidade.value++;
}
function contadorSub(){
  quantidade.value--
}

</script>

<template>
  <header>
    <nav>
      <div class="logo">
        <a href="App.vue"><img src="/img/logo.png" alt="logo"></a>
      </div>

      <div class="barra">
        <form action="#" method="get">
          <p>
            <input type="text" id="barra-pesquisa" placeholder="Pesquisar" />
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
      <div class="banner">
        <div class="eric">
          <h1>Eric-Emanuel Schmitt</h1>

          <p>
            Eric-Emmanuel Schmitt has been awarded more than 20 literary prizes and distinctions,
            and in 2001 he received the title of Chevalier des Arts et des Lettres. His books have
            been translated into over 40 languages.
          </p>

          <button class="verde">Acessar página do livro</button>
        </div>
        <div><img src="/img/livros/nog-ognia.png" /></div>
      </div>
      <div class="frete">
        <ul>
          <li><i class="fa-solid fa-truck"></i>Frete grátis para SC</li>
          <hr />
          <li><i class="fa-solid fa-star"></i>Livros recomendados</li>
          <hr />
          <li><i class="fa-solid fa-book"></i>Mais vendidos</li>
        </ul>
      </div>

      <section class="lancamentos">
        <h2>Lançamentos</h2>
        <div>
          <div v-for="livro in Livros" :key="livro.id">
            <img :src="livro.img" />
            <h3 class="title">{{ livro.titulo }} </h3>
            <p class="autor">{{ livro.autor }}</p>
            <p class="preco">R$ {{ livro.preco.toFixed(2) }}</p>
            <button class="verde"  @click="AdicionarCarrinho(livro)">
              <span class="fi fi-sr-shopping-cart"></span>
              <p>Comprar</p>
            </button>
          </div>
        </div>
      </section>

    </div>

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
        <div  class="adicionado" v-for="adicionado in Carrinho" :key="adicionado.id">
          <div>
          <img :src="adicionado.img" height="150" width="100">
          </div>
          <div>
          <h1> {{ adicionado.titulo }} </h1>
          <p> {{ adicionado.autor }} </p>
          <p> {{ adicionado.preco }} </p>
          <div class="quantidade">
          <button @click="contadorSom">+</button> {{ quantidade }} <button @click="contadorSub">-</button>
          </div>
          <div class="sub">

          </div>
          </div>

        </div>

        <button class="voltar">Voltar para loja</button>
        <p>
          <input type="text" placeholder="Código do Cupom" /><button class="verde">
            Inserir Cupom
          </button>
        </p>
        <div class="total">
          <h2>Total da Compra</h2>
          <ul>
            <li>
              <p>
                Produtos:<span> R${{ totalCompras.produtos }}</span>
              </p>
              <hr />
            </li>
            <li>
              <p>
                Frete: <span> {{ totalCompras.frete }}</span>
              </p>
              <hr />
            </li>
            <li>
              <p>
                Total: <span> R${{ totalCompras.total }} </span>
              </p>
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
  color: #27ae60;
  font-size: 2vw;
  font-weight: bold;
  margin: 0 0 3vw 0;
}

.adicionar ul {
  display: flex;
  justify-content: space-between;
  border-bottom: #27ae60 solid 2px;
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
  background-color: #f1f1f1;
  justify-content: space-between;
  padding: 7px 1vw 0.5vw 1vw;
  margin: 0 0 0 0;
}

header nav div.barra form p input {
  border: none;
  background: #f1f1f1;
  color: #b8b8b8;
  font-size: 1rem;
  padding: 0 1vw 0 0;
  outline: none;
}

/* PAGINAS */

header nav div.paginas ul {
  display: flex;
}

header nav div.paginas ul li a {
  color: #7b7881;
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
  color: #27ae60;
}

.invisible {
  display: none;
}

/* LANÇAMENTOS */

section.lancamentos {
  margin: 8.5vw;
}

section.lancamentos h2 {
  font-size: 2.4rem;
}

section.lancamentos>div {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 5vw 0 0 0;
}




section.lancamentos>div>div {
  margin: 0 3vw 2vw 0;
  width: 14.641288433382138vw;
}

section.lancamentos div h3 {
  margin: 1.5vw 0 1vw 0;
  font-weight: 450;
  font-size: 1.5vw;
  white-space: nowrap;         /* Não permite quebra de linha */
  overflow: hidden;            /* Esconde o texto que passar da largura */
  text-overflow: ellipsis;     /* Adiciona "..." no final do texto cortado */

}

section.lancamentos div p.autor{
  margin: 0.5vw 0 0.5vw 0;
  color: #4F4C57;
  font-size: 1.1vw;
}

section.lancamentos div p.preco{
  font-size: 1.25vw;
  font-weight: 500;
  margin: 1vw 0 2vw 0;
}

section.lancamentos div button{
  display: flex;
  font-size: 1.1vw;
  padding: 0.7vw 4.7vw 0.7vw 4.7vw;
  border: none;
  border-radius: 5px;
}

section.lancamentos div img{
  width: 14.641288433382138vw;
  height: 21.961932650073205vw;
  object-fit: cover;
  position: relative;
  border-radius: 5px;
}

/*========================= banner =========================*/
.banner {
  display: flex;
  justify-content: space-between;
}
.eric {
  padding: 8.5vw;
}
.eric h1 {
  font-size: 3.5vw;
  font-weight: bold;
  margin: 0 0 2vw 0;
}
.eric p {
  padding: 0 23vw 0 0;
  margin: 0 0 2vw 0;
  font-weight: 350;
}
.frete {
  border-top: #27ae60 solid 2px;
  border-bottom: #27ae60 solid 2px;
  padding: 5vw;
}
.frete i {
  font-size: 2.5vw;
  margin: 0 5px 0 0;
}
.frete ul {
  display: flex;

.frete li {
  font-size: 1.5vw;
}
/*========================= Carrinho2 =========================*/
.adicionado {
  display: flex;
  padding: 2.5vw;
  border-bottom: #b8b8b8 solid 2px;
}
.adicionado img {
  margin: 0 1vw 0 0;
}
.adicionado h1 {
  font-size: 1.5vw;
  font-weight: bold;
}
.adicionado p {
  margin: 1vw 0 1vw 0;
}

</style>

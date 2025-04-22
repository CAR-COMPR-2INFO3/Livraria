<script setup>

import { ref, computed } from 'vue';

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
const Carrinho = ref([]);
function AdicionarCarrinho() {
    Carrinho.value.push(Livros.value[0]);
}
function RemoverCarrinho() {
    Carrinho.value.pop();
}

</script>

<template>

    <header>
        <nav>
            <div>
                <a href="App.vue">IFbooks | Apreço a leitura</a>
            </div>

            <div>
                <form action="#" method="get">
                    <p>
                        <input type="text" id="barra-pesquisa" placeholder="Pesquisar">
                        <button type="submit">
                            <i class="fi fi-sr-shopping-cart"></i>
                        </button>
                    </p>
                </form>
            </div>
            <div>
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
            <div>
                <ul>
                    <li>
                        <p><i class="fi fi-sr-shopping-cart"></i></p>
                    </li>
                    <li>
                        <p><i class="fi fi-ss-heart"></i></p>
                    </li>
                    <li>
                        <p><i class="fi fi-sr-user"></i></p>
                    </li>
                </ul>
            </div>
        </nav>
    </header>

    <main>
        <section class="autor"></section>
        <div>
            <p>Autor de abril</p>
            <h1>{{ Livros[0].autor }}</h1>
        </div>
    </main>



</template>

<style scoped></style>

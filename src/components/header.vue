<script setup>
import { ref, computed } from 'vue';

const carrinhoAparecer = ref(false);
const botao = computed(() => 
  carrinhoAparecer.value ? 'Esconder' : 'Mostrar',
);

</script>

<template>

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
                            <button @click="carrinhoAparecer=!carrinhoAparecer">{{botao}}
                                <span class="fi fi-sr-shopping-cart"></span>
                            </button>
                        </p>
                    </li>
                    <li>
                        <p>|</p>
                    </li>
                    <li>
                        <p>
                            <a href="#"><span class="fi fi-sr-heart"></span></a>
                        </p>
                    </li>
                    <li>
                        <p>|</p>
                    </li>
                    <li>
                        <p><a href="#"><span class="fi fi-sr-user"></span></a></p>
                    </li>
                </ul>
            </nav>
        </div>
    </nav>
    <hr />


</template>

<style scoped>
/*    CSS RESET      */


/* http://meyerweb.com/eric/tools/css/reset/ 
   v2.0 | 20110126
   License: none (public domain)
*/

html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
}

/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
    display: block;
}

body {
    line-height: 1;
}

ol,
ul {
    list-style: none;
}

blockquote,
q {
    quotes: none;
}

blockquote:before,
blockquote:after,
q:before,
q:after {
    content: '';
    content: none;
}

table {
    border-collapse: collapse;
    border-spacing: 0;
}




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

header nav div.icones nav ul li p a {
    color: green;
}

hr {
    color: #27AE60;
}
</style>

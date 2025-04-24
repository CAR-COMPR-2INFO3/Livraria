<script setup>

</script>

<template>

    <nav>
        <div class="logo">
            <a href="App.vue">IFbooks <span class="linha">|</span> <span class="texto">Apreço a leitura</span></a>
        </div>

        <div class="barra">
            <form action="#" method="get">
                <p>
                    <input type="text" id="barra-pesquisa" placeholder="Pesquisar">
                    <button type="submit">
                        <img src="/public/img/Icon.png" alt="pesquisa"></img>
                    </button>
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
            <ul>
                <li>
                    <p><i class="fi fi-sr-shopping-cart"></i> | </p>
                </li>
                <li>
                    <p><i class="fi fi-sr-heart"></i> | </p>
                </li>
                <li>
                    <p><i class="fi fi-sr-user"></i></p>
                </li>
            </ul>
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

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}




/* GERAL */

header nav {
    margin: 2%;
    display: flex;
    justify-content: space-between;
}

/* LOGO */

header nav div.logo {
    font-size: 2rem;
}

header nav div.logo .linha{
    color: #27AE60;
    font-size: 2.5rem;
}

header nav div.logo .texto{
    color: #27AE60;
    font-size: 20px;
}



/* BARRA */

header nav div.barra form p input{
    border: none;
}

header nav div.barra form p button{
    border: none;
}

/* PAGINAS */

header nav div.paginas ul{
    display: flex;
}

header nav div.paginas ul li{
    padding: 0 3vw 0 0;
}


/* ICONES */

header nav div.icones ul{
    display: flex;
}








</style>

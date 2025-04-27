<script setup>
</script>
<template>
  <div class="footer">
    <div class="all">
      <div class="if">
        <p>IFbooks</p>
        <ul>
          <li><i class="fa-brands fa-square-facebook"></i></li>
          <li><i class="fa-brands fa-square-instagram"></i></li>
          <li><i class="fa-brands fa-square-twitter"></i></li>
        </ul>
      </div>
      <div class="contato">
        <p class="c">contato</p>
        <ul class="icone">
          <li><i class="fa-solid fa-phone"></i>
            <p>+55 47 40045263</p>
          </li>
          <li><i class="fa-solid fa-clock"></i>
            <p>8h às 23h - Seg a Sex</p>
          </li>
          <li><i class="fa-solid fa-envelope"></i>
            <p>contato@ifbooks.com</p>
          </li>
        </ul>
        <ul class="cartao">
          <li><img src="/public/img/pelpal.png" alt="pelpal"></li>
          <li><img src="/public/img/Mcard.png" alt="mastercard"></li>
          <li><img src="/public/img/visa.png" alt="visa"></li>
        </ul>
      </div>
    </div>
    <div class="final">
      <p class="dir">© Alguns direitos reservados. IFbooks 2025. </p>
    </div>
  </div>

</template>

<style scoped>
.if i {
  font-size: 2vw;
}

.if p {
  margin: 0 0 1vw 0;
}

.if ul {
  display: flex;
}

.if li {
  margin: 0 1vw 0 0;
}

.footer {
  color: white;
  background-color: #27AE60;
  padding: 40px 40px 10px 40px;
  justify-content: space-between;
}

.contato p.c {
  font-weight: bold;
  padding: 0 0 3.5vw 0;
}

.icone li {
  display: flex;
  margin: 0 0 0.1vw 0;
}

.icone i {
  font-size: 1.2vw;
  margin: 0 1vw 1.6vw 0;
}

.cartao {
  display: flex;
  margin: 2vw 0 0 0;
}

.cartao li {
  margin: 0 1vw 0 0;
}

.final {
  margin: 0vw 0 0 0;
  text-align: center;
  border-top: white solid 2px;
}
.final p {
  margin: 1.5vw 0 1.5vw 0;
}
.all{
  display: flex;
  justify-content: space-between;
}
</style>

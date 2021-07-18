<template>
  <footer class="footer">
    <span class="footer__contact">
      Hola, soy Miguel el autor del contenido. Envíame un correo si deseas
      contactar a mi
      <a href="mailto:miguelbetancurgrisales@gmail.com">email</a>
    </span>
    <span class="footer__copyright">
      © 2021 — Autor del sitio web:
      <a href="https://twitter.com/MBetancur22">Mateo</a>
    </span>
  </footer>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.footer {
  display: flex;
  flex-direction: column;
  text-align: center;
  bottom: 0;
  background-color: $second-color;
  padding: 40px 1rem 20px;
  color: $third-color;
  line-height: 1.5;
  font-size: 0.9rem;

  &__contact a {
    color: rgb(0, 197, 142);
    text-decoration: none;
  }

  &__copyright {
    margin-top: 1rem;
    color: rgb(99, 98, 98);
    font-size: 0.8rem;
    a {
      color: rgb(7, 160, 117);
      text-decoration: none;
    }
  }
}
</style>
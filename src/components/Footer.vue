<template>
  <footer class="footer">
    <p class="footer-label">Make Your Burguer &copy 2022</p>
  </footer>
</template>

<script>
export default { name: "Footer" };
</script>

<style scoped>
/* -------------- */
/* --- FOOTER --- */
/* -------------- */
.footer {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #222;
  height: 9.6rem;
  border-top: 4px solid #111;
}

.footer-label {
  font-size: 1.4rem;
  color: #fcba03;
}
</style>

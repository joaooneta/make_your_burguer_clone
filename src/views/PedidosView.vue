<template>
  <main>
    <section class="section-ordered ordered-container">
      <h2 class="heading heading-secondary">Gerenciar Pedidos</h2>
      <Dashboard />
    </section>
  </main>
</template>

<script>
import Dashboard from "../components/Dashboard.vue";

export default {
  name: "PedidosView",
  components: { Dashboard },
};
</script>

<style scoped>
.ordered-container {
  max-width: 120rem;
  padding: 0 3.2rem;
  margin: 0 auto;
  display: grid;
  justify-content: center;
}
</style>

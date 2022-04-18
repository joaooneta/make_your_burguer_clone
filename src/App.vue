<script>
import Navbar from "../src/components/Navbar.vue";
import Footer from "../src/components/Footer.vue";

export default {
  components: { Navbar, Footer },
};
</script>

<template>
  <header>
    <Navbar />
  </header>

  <RouterView />
  <Footer />
</template>

<style></style>

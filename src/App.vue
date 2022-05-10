<template>
  <header>
    <Navbar :logo="logo_src" :alt="app_name" />
  </header>

  <RouterView />
  <Footer />
</template>

<script>
import Navbar from "../src/components/Navbar.vue";
import Footer from "../src/components/Footer.vue";

export default {
  components: { Navbar, Footer },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burguer",
    };
  },
};
</script>

<style>
/* ----------------- */
/* ---- GENERAL ---- */
/* ----------------- */

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}

body {
  font-family: "Rubik", sans-serif;
  line-height: 1;
  font-weight: 400;
}

/* ---------------- */
/* --- REUSABLE --- */
/* ---------------- */
.heading {
  font-weight: 700;
  color: #333;
  letter-spacing: -0.5px;
  text-align: center;
}

.heading-secondary {
  font-size: 4.4rem;
  line-height: 1.2;
  margin-bottom: 4.8rem;
  margin-top: 4.8rem;
}
</style>

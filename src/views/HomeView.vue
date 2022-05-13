<template>
  <main>
    <section class="hero-section">
      <TheBanner />
    </section>
    <section class="montar-section">
      <div class="container">
        <BurguerForm />
      </div>
    </section>
  </main>
</template>

<script>
import TheBanner from "../components/TheBanner.vue";
import BurguerForm from "../components/BurguerForm.vue";

export default {
  name: "Home",
  components: { TheBanner, BurguerForm },
};
</script>

<style scoped>
/* -------------------- */
/* --- HERO SECTION --- */
/* -------------------- */
.hero-section {
  margin-bottom: 8.6rem;
}

/* ------------------------------ */
/* --- MONTAR BURGUER SECTION --- */
/* ------------------------------ */
.montar-section {
  max-width: 120rem;
  padding: 0 3.2rem;
  margin: 0 auto;
  display: flex;
  justify-content: center;
}
</style>

<template>
  <section class="hero-section">
    <div class="hero-container">
      <h1 class="heading">Make Your Burguer</h1>
    </div>
  </section>
</template>

<script>
export default {
  name: "Hero",
};
</script>

<style>
/* -------------------- */
/* --- HERO SECTION --- */
/* -------------------- */
.hero-container {
  background-image: url("../../public/img/burger.jpg");
  background-position: 0 -25rem;
  background-size: cover;
  background-repeat: no-repeat;
  height: 74rem;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.heading {
  font-weight: 700;
  color: #fff;
  font-size: 5.2rem;
  letter-spacing: -0.5px;
  text-align: center;
  background-color: #222;
  padding: 2rem 4rem;
}
</style>

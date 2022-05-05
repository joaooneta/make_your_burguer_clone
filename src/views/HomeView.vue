<template>
  <main>
    <HeroSection />
    <MontarBurguerSection />
  </main>
</template>

<script>
import HeroSection from "../components/HeroSection.vue";
import MontarBurguerSection from "../components/MontarBurguerSection.vue";

export default {
  name: "Home",
  components: {
    HeroSection,
    MontarBurguerSection,
  },
};
</script>

<style scoped></style>

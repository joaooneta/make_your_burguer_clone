<template>
  <header class="header">
    <RouterLink to="/">
      <img class="logo" :src="logo" :alt="alt" />
    </RouterLink>
    <nav class="header-nav">
      <ul class="header-nav-list">
        <li>
          <RouterLink to="/" class="header-nav-link">Home</RouterLink>
        </li>
        <li>
          <RouterLink to="/pedidos" class="header-nav-link">Pedidos</RouterLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script scoped>
export default {
  name: "TheHeader",
  props: ["logo", "alt"],
};
</script>

<style scoped>
/* ---------------- */
/* ---- HEADER ---- */
/* ---------------- */
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #222;
  border-bottom: 4px solid #111;
  height: 9.6rem;
  padding: 0 4.8rem;
}

.logo {
  height: 4.4rem;
}

/* -------------------- */
/* ---- NAVIGATION ---- */
/* -------------------- */
.header-nav-list {
  display: flex;
  list-style: none;
  gap: 3.2rem;
  align-items: center;
}

.header-nav-link:link,
.header-nav-link:visited {
  display: inline-block;
  text-decoration: none;
  color: #fcba03;
  font-weight: 500;
  font-size: 1.8rem;
  transition: all 0.3s;
}

.header-nav-link:hover,
.header-nav-link:active {
  color: #fff;
}
</style>

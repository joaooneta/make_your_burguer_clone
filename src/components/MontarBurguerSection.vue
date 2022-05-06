<template>
  <section class="montar-section">
    <div class="container">
      <h2 class="heading-secondary">Monte o seu burger:</h2>
      <form class="burguer-form" action="#">
        <div>
          <label for="nome">Nome do cliente:</label>
          <input
            type="text"
            name="nome"
            id="nome"
            placeholder="Digite o seu nome"
          />
        </div>

        <div>
          <label for="select-bread">Escolha o pão:</label>
          <select
            name="select-bread"
            id="select-bread"
            v-model="bread"
            required
          >
            <option value="">Escolha uma opção:</option>
            <option v-for="bread in breads" :key="bread.id" :value="bread.tipo">
              {{ bread.tipo }}
            </option>
          </select>
        </div>

        <div>
          <label for="select-meat">Escolha a carne do seu Burger:</label>
          <select name="select-meat" id="select-meat" v-model="meat" required>
            <option value="">Escolha uma opção:</option>
            <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">
              {{ meat.tipo }}
            </option>
          </select>
        </div>

        <div>
          <label for="checkbox-optionals">Escolha os opcionais:</label>
          <div class="optionals-container">
            <div
              class="option-box"
              v-for="optional in optionalsData"
              :key="optional.id"
            >
              <input
                type="checkbox"
                name="checkbox-optionals"
                v-model="optinals"
                :value="optional.tipo"
              />
              <span class="option-span">{{ optional.tipo }}</span>
            </div>
          </div>
        </div>

        <div>
          <input type="submit" value="Criar meu burguer!" class="btn-form" />
        </div>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  name: "MontarBurguerForm",
  data() {
    return {
      breads: null,
      meats: null,
      optionalsData: null,
      clientName: null,
      bread: null,
      meat: null,
      optionals: [],
      status: "Solicitado",
      msg: null,
    };
  },
  methods: {
    async getIngredients() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.breads = data.paes;
      this.meats = data.carnes;
      this.optionalsData = data.opcionais;
    },
  },
  mounted() {
    this.getIngredients();
  },
};
</script>

<style scoped>
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

.burguer-form label {
  display: block;
  font-size: 1.6rem;
  font-weight: 600;
  margin-bottom: 1.6rem;
  padding: 0.5rem 1rem;
  border-left: 3px solid #fcba03;
}

.burguer-form input,
.burguer-form select {
  width: 70%;
  font-family: inherit;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  margin-bottom: 3rem;
}

.optionals-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-column: start;
}

.option-box input,
.option-box span {
  width: auto;
  font-weight: 700;
}

.option-span {
  font-size: 1.6rem;
  margin-left: 0.6rem;
}

.btn-form {
  font-size: 1.6rem;
  background-color: #222;
  color: #fcba03;
  font-weight: 700;
  border: 2px solid #222;
  padding: 1rem;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.btn-form:hover {
  background-color: transparent;
  color: #222;
}
</style>

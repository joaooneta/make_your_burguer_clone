<template>
  <h2 class="heading-secondary">Monte o seu burger:</h2>
  <Message :message="message" v-show="message" />
  <form class="burguer-form" @submit="createBurguer">
    <div>
      <label for="nome">Nome do cliente:</label>
      <input
        type="text"
        name="nome"
        id="nome"
        placeholder="Digite o seu nome"
        v-model="clientName"
      />
    </div>

    <div>
      <label for="select-bread">Escolha o pão:</label>
      <select name="select-bread" id="select-bread" v-model="bread" required>
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
            id="checkbox-optionals"
            v-model="optionals"
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
</template>

<script>
import Message from "./Message.vue";

export default {
  name: "MontarBurguerForm",
  components: { Message },
  data() {
    return {
      breads: null,
      meats: null,
      optionalsData: null,
      clientName: null,
      bread: null,
      meat: null,
      optionals: [],
      message: null,
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
    async createBurguer(event) {
      event.preventDefault();

      const data = {
        clientName: this.clientName,
        bread: this.bread,
        meat: this.meat,
        optionals: Array.from(this.optionals),
        status: "Solicitado",
      };

      const dataJSON = JSON.stringify(data);
      const req = await fetch(" http://localhost:3000/burgers", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: dataJSON,
      });

      const res = await req.json();

      this.message = `Pedido Nº ${res.id} realizado com sucesso!`;
      setTimeout(() => (this.message = ""), 3000);

      this.clientName = "";
      this.bread = "";
      this.meat = "";
      this.optionals = "";
    },
  },
  mounted() {
    this.getIngredients();
  },
};
</script>

<style scoped>
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

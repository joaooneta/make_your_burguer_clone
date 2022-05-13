<template>
  <Message :message="message" v-show="message" />
  <table class="dashboard-table">
    <thead>
      <tr>
        <th>#:</th>
        <th>Cliente:</th>
        <th>Pão:</th>
        <th>Carne:</th>
        <th>Opcionais:</th>
        <th>Ações:</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="burger in burgers" :key="burger.id">
        <td>{{ burger.id }}</td>
        <td>{{ burger.clientName }}</td>
        <td>{{ burger.bread }}</td>
        <td>{{ burger.meat }}</td>
        <td>
          <ul>
            <li v-for="(optionals, index) in burger.optionals" :key="index">
              {{ optionals }}
            </li>
          </ul>
        </td>
        <td>
          <select name="" id="" @change="updateBurger($event, burger.id)">
            <option value="">Selecione:</option>
            <option
              v-for="s in status"
              :key="s.id"
              :value="s.tipo"
              :selected="burger.status == s.tipo"
            >
              {{ s.tipo }}
            </option>
          </select>
          <button class="btn-delete" @click="deleteBurger(burger.id)">
            Cancelar
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import Message from "./Message.vue";

export default {
  name: "Dashboard",
  components: { Message },
  data() {
    return {
      burgers: null,
      burguer_id: null,
      status: [],
      message: null,
    };
  },
  methods: {
    async getPedidos() {
      const req = await fetch("http://localhost:3000/burgers");
      const data = await req.json();

      this.burgers = data;

      this.getStatus();
    },
    async getStatus() {
      const req = await fetch("http://localhost:3000/status");
      const data = await req.json();

      this.status = data;
    },
    async deleteBurger(id) {
      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE",
      });

      const res = await req.json();

      this.message = `O pedido Nº ${id} foi removido com sucesso`;
      setTimeout(() => (this.message = ""), 3000);

      this.getPedidos();
    },
    async updateBurger(event, id) {
      const option = event.target.value;
      const dataJson = JSON.stringify({ status: option });

      const req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: dataJson,
      });

      const res = await req.json();
      this.message = `O pedido Nº ${res.id} foi atualizado para ${res.status}`;
      setTimeout(() => (this.message = ""), 3000);
    },
  },
  mounted() {
    this.getPedidos();
  },
};
</script>

<style scoped>
.dashboard-table {
  border-collapse: collapse;
  margin: 2.5rem 0;
  min-width: 120rem;
  font-size: 1.8rem;
}

.dashboard-table thead tr {
  font-size: 1.6;
  color: #333;
  font-weight: 600;
  text-align: left;
  border-bottom: 3px solid #333;
}

.dashboard-table th,
.dashboard-table td {
  padding: 1.2rem 1.5rem;
  border-bottom: 1px solid #777;
}

select {
  padding: 1.2rem 0.6rem;
  margin-right: 1.2rem;
}

.btn-delete {
  background-color: #333;
  color: #fcba03;
  font-weight: 700;
  border: 2px solid #222;
  padding: 1rem;
  font-size: 1.6rem;
  margin: 0 auto;
  cursor: pointer;
  transition: all 0.3s;
}

.btn-delete:hover {
  background-color: transparent;
  color: #222;
}
</style>

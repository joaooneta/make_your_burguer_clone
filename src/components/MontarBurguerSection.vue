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
          <label for="select-bread">Escolha o pao:</label>
          <select name="select-bread" id="select-bread" required>
            <option value="">Escolha uma opção:</option>
            <option value="1">Italiano Branco</option>
            <option value="2">3 Queijos</option>
            <option value="3">Parmesao e Orégano</option>
            <option value="4">Integral</option>
          </select>
        </div>

        <div>
          <label for="select-meat">Escolha a carne do seu Burger:</label>
          <select name="select-meat" id="select-meat" required>
            <option value="">Escolha uma opção:</option>
            <option value="1">Maminha</option>
            <option value="2">Alcatra</option>
            <option value="3">Picanha</option>
            <option value="4">Veggie burger</option>
          </select>
        </div>

        <div>
          <label for="checkbox-optionals">Escolha os opcionais:</label>
          <div class="optionals-container">
            <div class="option-box">
              <input
                type="checkbox"
                name="checkbox-optionals"
                id="checkbox-optionals"
                value="bacon"
              />
              <span class="option-span">Bacon</span>
            </div>

            <div class="option-box">
              <input
                type="checkbox"
                name="checkbox-optionals"
                id="checkbox-optionals"
                value="cheddar"
              />
              <span class="option-span">Cheddar</span>
            </div>

            <div class="option-box">
              <input
                type="checkbox"
                name="checkbox-optionals"
                id="checkbox-optionals"
                value="salame"
              />
              <span class="option-span">Salame</span>
            </div>

            <div class="option-box">
              <input
                type="checkbox"
                name="checkbox-optionals"
                id="checkbox-optionals"
                value="tomate"
              />
              <span class="option-span">Tomate</span>
            </div>

            <div class="option-box">
              <input
                type="checkbox"
                name="checkbox-optionals"
                id="checkbox-optionals"
                value="cebola-roxa"
              />
              <span class="option-span">Cebola roxa</span>
            </div>

            <div class="option-box">
              <input
                type="checkbox"
                name="checkbox-optionals"
                id="checkbox-optionals"
                value="pepino"
              />
              <span class="option-span">Pepino</span>
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

<script></script>

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

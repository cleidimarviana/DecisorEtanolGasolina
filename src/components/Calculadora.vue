<template>
  <div id="app">
    <h1>Etanol ou Gasolina?</h1>
    <form @submit.prevent="calculateBestOption">
      <div class="form-group">
        <label for="gasPrice">Preço da Gasolina (R$):</label>
        <input type="number" id="gasPrice" v-model="gasPrice" required step="0.01" />
      </div>
      <div class="form-group">
        <label for="ethanolPrice">Preço do Álcool (R$):</label>
        <input type="number" id="ethanolPrice" v-model="ethanolPrice" required step="0.01" />
      </div>
      <button type="submit" class="calculate-button">Calcular</button>
    </form>
    <div v-if="result" class="result">
      <p>{{ result }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalculadoraComponent',

  data() {
    return {
      gasPrice: 0,
      ethanolPrice: 0,
      result: '',
    };
  },
  methods: {
    calculateBestOption() {
      const ratio = this.ethanolPrice / this.gasPrice;
      if (ratio < 0.7) {
        this.result = 'É mais viável abastecer com álcool.';
      } else {
        this.result = 'É mais viável abastecer com gasolina.';
      }
    },
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  padding: 20px;
  max-width: 500px;
  margin: 60px auto;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  background-color: #fff;
}
h1 {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}
form {
  margin: 20px 0;
}
.form-group {
  margin-bottom: 15px;
}
label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}
input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 5px;
  box-sizing: border-box;
}
button.calculate-button {
  display: block;
  width: 100%;
  padding: 10px;
  font-size: 16px;
  color: #fff;
  background-color: #007bff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 20px;
}
button.calculate-button:hover {
  background-color: #0056b3;
}
.result {
  margin-top: 20px;
  font-size: 18px;
  font-weight: bold;
  color: #007bff;
}
</style>

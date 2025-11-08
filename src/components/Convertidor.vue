<template>
  <div class="conversor-container">
    <div class="card">
      <h2>💱 Conversor de Divisas</h2>

      <div class="form-group">
        <label for="cantidad">Ingrese Cantidad</label>
        <input id="cantidad" v-model.number="cantidad" type="number" min="0" />
      </div>

      <div class="form-row">
        <div class="form-group">
          <label for="tengo">Tengo</label>
          <select id="tengo" v-model="monedaOrigen">
            <option value="USD">USD - Dolar estadounidense</option>
            <option value="ARS">ARS - Peso argentino</option>
            <option value="EUR">EUR - Euro</option>
            <option value="BRL">BRL - Real brasileño</option>
            <option value="GBP">GBP - Libra esterlina</option>
            <option value="CLP">CLP - Peso chileno</option>
            <option value="UYU">UYU - Peso uruguayo</option>
          </select>
        </div>

        <div class="form-group">
          <label for="quiero">Quiero</label>
          <select id="quiero" v-model="monedaDestino">
            <option value="USD">USD - Dolar estadounidense</option>
            <option value="ARS">ARS - Peso argentino</option>
            <option value="EUR">EUR - Euro</option>
            <option value="BRL">BRL - Real brasileño</option>
            <option value="GBP">GBP - Libra esterlina</option>
            <option value="CLP">CLP - Peso chileno</option>
            <option value="UYU">UYU - Peso uruguayo</option>

          </select>
        </div>
      </div>

      <button @click="convertir">Convertir</button>

      <p v-if="resultado !== null" class="resultado">
        {{ cantidad }} {{ monedaOrigen }} = <strong>{{ resultado.toFixed(2) }} {{ monedaDestino }}</strong>
      </p>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        cantidad: 0,
        monedaOrigen: 'USD',
        monedaDestino: 'EUR',
        tasas: { USD: 1, ARS: 1443, EUR: 1674, BRL: 260 , GBP: 1965 , CLP: 1.45 , UYU: 36},
        resultado: null
      }
    },
    methods: {
      convertir() {
        const enUSD = this.cantidad / this.tasas[this.monedaOrigen]
        this.resultado = enUSD * this.tasas[this.monedaDestino]
      }
    }
  }
</script>

<style scoped>
  .conversor-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 80vh;
    background: #1e1e1e;
  }

  .card {
    background: #2c2c2c;
    padding: 30px 40px;
    border-radius: 16px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.4);
    color: #fff;
    text-align: center;
    width: 350px;
  }

  h2 {
    color: #42b983;
    margin-bottom: 20px;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-bottom: 15px;
  }

  .form-row {
    display: flex;
    justify-content: space-between;
    gap: 10px;
  }

  label {
    font-weight: bold;
    margin-bottom: 6px;
  }

  input, select {
    width: 100%;
    padding: 8px;
    border-radius: 6px;
    border: 1px solid #444;
    background: #333;
    color: #fff;
    outline: none;
  }

    input:focus, select:focus {
      border-color: #42b983;
    }

  button {
    width: 100%;
    background: #42b983;
    color: white;
    border: none;
    border-radius: 6px;
    padding: 10px;
    font-weight: bold;
    cursor: pointer;
    transition: 0.3s;
  }

    button:hover {
      background: #3ca174;
    }

  .resultado {
    margin-top: 15px;
    font-size: 1.1em;
  }
</style>

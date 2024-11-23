<template>
    <div class="currency-converter">
      <!-- Pantalla para mostrar el monto ingresado -->
      <div class="screen">
        <p>{{ amount || "0" }} {{ fromCurrency }}</p>
      </div>
  
      <!-- Pantalla para mostrar el resultado de la conversión -->
      <div class="screen result-screen">
        <p>{{ convertedAmount !== null ? convertedAmount + " " + toCurrency : "Resultado" }}</p>
      </div>
  
      <!-- Entrada de datos -->
      <div class="inputs">
        <input
          type="number"
          v-model.number="amount"
          placeholder="Ingrese monto"
        />
        <select v-model="fromCurrency">
          <option value="USD">USD - Dólar Estadounidense</option>
          <option value="EUR">EUR - Euro</option>
          <option value="GBP">GBP - Libra Esterlina</option>
          <option value="JPY">JPY - Yen Japonés</option>
          <option value="PEN">PEN - Sol Peruano</option>
        </select>
        <select v-model="toCurrency">
          <option value="USD">USD - Dólar Estadounidense</option>
          <option value="EUR">EUR - Euro</option>
          <option value="GBP">GBP - Libra Esterlina</option>
          <option value="JPY">JPY - Yen Japonés</option>
          <option value="PEN">PEN - Sol Peruano</option>
        </select>
      </div>
  
      <!-- Botones -->
      <div class="buttons">
        <button @click="convert">Convertir</button>
        <button @click="clear">C</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "ConvertidorMonedas",
    data() {
      return {
        amount: null, // Monto ingresado
        fromCurrency: "USD", // Moneda de origen
        toCurrency: "USD", // Moneda de destino
        convertedAmount: null, // Monto convertido
        exchangeRates: {
          USD: { USD: 1, EUR: 0.94, GBP: 0.82, JPY: 147.18, PEN: 3.85 },
          EUR: { USD: 1.06, EUR: 1, GBP: 0.87, JPY: 156.36, PEN: 4.10 },
          GBP: { USD: 1.22, EUR: 1.15, GBP: 1, JPY: 180.17, PEN: 4.70 },
          JPY: { USD: 0.0068, EUR: 0.0064, GBP: 0.0056, JPY: 1, PEN: 0.026 },
          PEN: { USD: 0.26, EUR: 0.24, GBP: 0.21, JPY: 38.46, PEN: 1 },
        },
      };
    },
    methods: {
      convert() {
        if (this.amount === null || isNaN(this.amount)) {
          this.convertedAmount = "Error";
          return;
        }
  
        const rate = this.exchangeRates[this.fromCurrency][this.toCurrency];
        this.convertedAmount = (this.amount * rate).toFixed(2); // Redondear a 2 decimales
      },
      clear() {
        this.amount = null;
        this.convertedAmount = null;
      },
    },
  };
  </script>
  
  <style scoped>
  .currency-converter {
    width: 300px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  /* Pantallas */
  .screen {
    height: 38px;
    margin-bottom: 10px;
    background-color: #333;
    color: #fff;
    font-size: 20px;
    font-family: monospace;
    text-align: center;
    padding: 10px;
    border-radius: 4px;
  }
  
  .result-screen {
    color: orange; /* Resultado en color naranja */
    font-size: 22px; /* Fuente más grande */
  }
  
  /* Entradas */
  .inputs {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-bottom: 20px;
  }
  input {
    padding: 10px;
    font-size: 16px;
    width: 100%;
    box-sizing: border-box;
  }
  select {
    padding: 10px;
    font-size: 16px;
    width: 100%;
    box-sizing: border-box;
  }
  
  /* Botones */
  .buttons {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  button {
    height: 50px;
    font-size: 18px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    background-color: #e0e0e0;
  }
  button:active {
    background-color: #d0d0d0;
  }
  button:nth-child(1) {
    background-color: #007bff;
    color: white;
  }
  button:nth-child(1):active {
    background-color: #0056b3;
  }
  </style>
  
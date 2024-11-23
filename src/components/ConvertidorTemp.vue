<template>
  <div class="converter">
    <!-- Pantalla para mostrar el dato ingresado -->
    <div class="screen">
      <p>{{ inputTemperature || "0" }} {{ inputUnit }}</p>
    </div>

    <!-- Pantalla para mostrar el resultado de la conversión -->
    <div class="screen result-screen">
      <p>{{ convertedTemperature !== null ? convertedTemperature + " " + outputUnit : "" }}</p>
    </div>
    <div class="inputs">
      <input
        type="number"
        v-model.number="inputTemperature"
        placeholder="Ingrese temperatura"
      />
      <div>

      </div>
      <br><br>
      <select v-model="inputUnit">
        <option value="C">Celsius</option>
        <option value="F">Fahrenheit</option>
        <option value="K">Kelvin</option>
      </select>
      <select v-model="outputUnit">
        <option value="C">Celsius</option>
        <option value="F">Fahrenheit</option>
        <option value="K">Kelvin</option>
      </select>
    </div>
    <div class="buttons">
      <button @click="convert">Convertir</button>
      <button @click="clear">C</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TemperatureConverter",
  data() {
    return {
      inputTemperature: null, // Temperatura ingresada
      inputUnit: "C", // Unidad de entrada (por defecto Celsius)
      outputUnit: "C", // Unidad de salida (por defecto Celsius)
      convertedTemperature: null, // Temperatura convertida
    };
  },
  methods: {
    convert() {
      if (this.inputTemperature === null || isNaN(this.inputTemperature)) {
        this.convertedTemperature = "Error";
        return;
      }

      const temp = parseFloat(this.inputTemperature);
      let result;

      // Conversiones
      if (this.inputUnit === "C") {
        if (this.outputUnit === "F") result = (temp * 9) / 5 + 32;
        else if (this.outputUnit === "K") result = temp + 273.15;
        else result = temp;
      } else if (this.inputUnit === "F") {
        if (this.outputUnit === "C") result = ((temp - 32) * 5) / 9;
        else if (this.outputUnit === "K") result = ((temp - 32) * 5) / 9 + 273.15;
        else result = temp;
      } else if (this.inputUnit === "K") {
        if (this.outputUnit === "C") result = temp - 273.15;
        else if (this.outputUnit === "F") result = ((temp - 273.15) * 9) / 5 + 32;
        else result = temp;
      }

      this.convertedTemperature = result.toFixed(2); // Redondear a 2 decimales
    },
    clear() {
      this.inputTemperature = null;
      this.convertedTemperature = null;
    },
  },
};
</script>

<style scoped>
.converter {
  width: 300px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.screen {
  height: 75px;
  margin-bottom: 20px;
  background-color: #333;
  color: #fff;
  font-size: 20px;
  font-family: monospace;
  text-align: center;
  padding: 10px;
  border-radius: 4px;
}
.screen .result {
  color: orange; /* Cambia el color a naranja */
  font-size: 22px; /* Incrementa el tamaño de la fuente en 2 píxeles */
}
.inputs {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}
input {
  width: 60%;
  padding: 10px;
  font-size: 16px;
}
select {
  width: 35%;
  padding: 10px;
  font-size: 16px;
}
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

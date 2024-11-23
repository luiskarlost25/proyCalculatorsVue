<template>
  <div class="calculator">
    <div class="screen">{{ display }}</div>
    <div class="buttons">
      <!-- Números -->
      <button @click="appendNumber(7)">7</button>
      <button @click="appendNumber(8)">8</button>
      <button @click="appendNumber(9)">9</button>
      <button class="operator" @click="setOperation('/')">÷</button>

      <button @click="appendNumber(4)">4</button>
      <button @click="appendNumber(5)">5</button>
      <button @click="appendNumber(6)">6</button>
      <button class="operator" @click="setOperation('*')">×</button>

      <button @click="appendNumber(1)">1</button>
      <button @click="appendNumber(2)">2</button>
      <button @click="appendNumber(3)">3</button>
      <button class="operator" @click="setOperation('-')">-</button>

      <button @click="appendNumber(0)">0</button>
      <button @click="clear">C</button>
      <button @click="calculate">=</button>
      <button class="operator" @click="setOperation('+')">+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      current: "", // Cadena actual que se muestra
      operation: null, // Operación actual seleccionada
      previous: null, // Número anterior ingresado
    };
  },
  computed: {
    display() {
      return this.current || "0"; // Muestra 0 si no hay nada ingresado
    },
  },
  methods: {
    appendNumber(number) {
      this.current += number.toString();
    },
    setOperation(op) {
      if (this.current === "") return;
      this.operation = op;
      this.previous = this.current;
      this.current = "";
    },
    calculate() {
      if (!this.operation || this.current === "" || this.previous === null) return;

      const prev = parseFloat(this.previous);
      const curr = parseFloat(this.current);

      let result;
      switch (this.operation) {
        case "+":
          result = prev + curr;
          break;
        case "-":
          result = prev - curr;
          break;
        case "*":
          result = prev * curr;
          break;
        case "/":
          result = curr !== 0 ? prev / curr : "Error";
          break;
        default:
          return;
      }

      this.current = result.toString();
      this.operation = null;
      this.previous = null;
    },
    clear() {
      this.current = "";
      this.operation = null;
      this.previous = null;
    },
  },
};
</script>

<style scoped>
.calculator {
  width: 300px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.screen {
  height: 50px;
  margin-bottom: 20px;
  background-color: #333;
  color: #fff;
  font-size: 24px;
  font-family: monospace;
  text-align: right;
  padding: 10px;
  border-radius: 4px;
}
.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
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
button.operator {
  background-color: #f57c00;
  color: white;
}
button.operator:active {
  background-color: #e65100;
}
</style>

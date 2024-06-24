<!-- src/components/Operacao.vue -->
<template>
    <div class="operation">
      <input type="number" v-model="number1" placeholder="Insira o primeiro número">
      <select v-model="operation">
        <option value="add">+</option>
        <option value="subtract">-</option>
        <option value="multiply">*</option>
        <option value="divide">/</option>
      </select>
      <input type="number" v-model="number2" placeholder="Insira o segundo número">
      <button @click="calculate">Calcular</button>
    </div>
  </template>

  <script>
  export default {
    name: 'Operacao',
    data() {
      return {
        number1: 0,
        number2: 0,
        operation: 'add',
        result: 0
      }
    },
    methods: {
      calculate() {
        switch (this.operation) {
          case 'add':
            this.result = this.number1 + this.number2;
            break;
          case 'subtract':
            this.result = this.number1 - this.number2;
            break;
          case 'multiply':
            this.result = this.number1 * this.number2;
            break;
          case 'divide':
            this.result = this.number2 !== 0 ? this.number1 / this.number2 : 'Erro: Divisão por zero';
            break;
          default:
            this.result = 0;
        }
        this.$emit('update:result', this.result);
      }
    }
  }
  </script>

  <style scoped>
  .operation {
    text-align: center;
    margin-top: 20px;
  }

  input, select {
    margin: 5px;
    padding: 10px;
    font-size: 1em;
    width: calc(100% - 22px);
    box-sizing: border-box;
    border-radius: 5px;
  }

  button {
    margin-top: 10px;
    padding: 10px 20px;
    font-size: 1em;
    background-color: #206948;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #359a72;
  }

  @media (max-width: 600px) {
    .operation {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    input, select, button {
      width: 100%;
      margin: 5px 0;
    }
  }
  </style>

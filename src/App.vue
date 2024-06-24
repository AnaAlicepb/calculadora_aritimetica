<!-- src/App.vue -->
<template>
    <div id="app">
      <div class="container">
        <Cabecalho />
        <div class="calculator-wrapper">
          <Operacao ref="operacaoComponent" @update:result="updateResult" />
          <Resultado :result="result" />
        </div>
      </div>
    </div>
  </template>

  <script>
  import Cabecalho from './components/Cabecalho.vue'
  import Operacao from './components/Operacao.vue'
  import Resultado from './components/Resultado.vue'

  export default {
    name: 'App',
    components: {
      Cabecalho,
      Operacao,
      Resultado
    },
    data() {
      return {
        result: 0
      }
    },
    methods: {
      updateResult(newResult) {
        this.result = newResult;
      }
    }
  }
  </script>

  <style>
  body {
    margin: 0;
    padding: 0;
    font-family: 'Noto Sans JP';
  }

  #app {
    background-image: url('../public/img/background.jpg');
    background-size: cover;
    background-position: center;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #09335e;
    position: relative;
}

#app::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(7, 0, 0, 0.192);
    z-index: 1;
}

#app > * {
    position: relative;
    z-index: 2; /* Garante que o conteúdo esteja acima da sobreposição */
}


  .container {
    background-color: rgba(240, 235, 235, 0.8);
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    padding: 20px;
    width: 90%;
    max-width: 400px;
    text-align: center;
  }

  .calculator-wrapper {
    margin-top: 20px;
  }

  button {
    padding: 10px 20px;
    font-size: 16px;
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
    .container {
      width: 100%;
      margin: 10px;
      padding: 15px;
    }

    input, select, button {
      width: 100%;
      margin: 5px 0;
    }
  }
  </style>

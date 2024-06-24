<!-- src/components/Resultado.vue -->
<template>
    <div class="result">
      <h2>Resultado: {{ result }}</h2>
    </div>
  </template>

  <script>
  export default {
    name: 'Resultado',
    props: ['result']
  }
  </script>

  <style scoped>
  .result {
    text-align: center;
    margin-top: 20px;
  }
  h2 {
    color: #0a0a0a;
  }
  </style>

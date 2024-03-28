<script setup>

import { reactive } from 'vue';

const calc = reactive({
  valor1: '',
  valor2: '',
  resultado: '',
  operacao: 'soma',
});

function calcula() {

  const num1 = parseFloat(calc.valor1);
  const num2 = parseFloat(calc.valor2);


  if (isNaN(num1) || isNaN(num2)) {
    calc.resultado = "";
    return;
  }


  if (calc.operacao === 'soma') {
    calc.resultado = parseFloat(calc.valor1) + parseFloat(calc.valor2);
  } else if (calc.operacao === 'subtracao') {
    calc.resultado = parseFloat(calc.valor1) - parseFloat(calc.valor2);
  } else if (calc.operacao === 'multiplicacao') {
    calc.resultado = parseFloat(calc.valor1) * parseFloat(calc.valor2);
  } else if (calc.operacao === 'divisao') {
    calc.resultado = parseFloat(calc.valor1) / parseFloat(calc.valor2);
  }
}
</script>

<template>

  <div class="container">

    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet"
      integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <div>
      <h1>Calculadora aritmética</h1>
      <div class="p-3">
        <label for="operacao">Escolha a operação:</label>
        <select @change="calcula" v-model="calc.operacao" name="operacao">
          <option selected value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
      <div class="p-3">
        <input @keyup="calcula" v-model="calc.valor1" placeholder="Valor 1">
        <input @keyup="calcula" v-model="calc.valor2" placeholder="Valor 2">
        <h3 class="mt-3">Resultado: {{ calc.resultado }}</h3>
      </div>
    </div>
  </div>
</template>

<style scoped></style>

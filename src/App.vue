<script setup>
import { reactive } from 'vue'

  const estado = reactive({
    filtro: 'add',
    number1: 0,
    number2: 0,
  })

  function calculo() {
    const filtro = estado.filtro;

    switch (filtro) {
      case 'add':
        return parseFloat(estado.number1) + parseFloat(estado.number2)
      case 'sub':
        return parseFloat(estado.number1) - parseFloat(estado.number2)
      case 'mul':
        return parseFloat(estado.number1) * parseFloat(estado.number2)
      case 'div':
        return parseFloat(estado.number1) / parseFloat(estado.number2)
    }
  }

</script>

<template>

  <div class="container">
    <h1>Calculadora Aritmética</h1>
    <div class="container__area">
      <input class="operador" type="number" @keyup="evento => estado.number1 = evento.target.value">
      <select class="operador__select" @change="evento => estado.filtro = evento.target.value">
        <option class="container__operando" value="add">+</option>
        <option class="container__operando" value="sub">-</option>
        <option class="container__operando" value="mul">*</option>
        <option class="container__operando" value="div">/</option>
      </select>
      <input class="operador" type="number" name="" @keyup="evento => estado.number2 = evento.target.value">
    </div>
    <div>
      <h2>Resultado</h2>
      <span>{{ calculo() }}</span>
    </div>
  </div>

</template>

<style scoped>

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    text-align: center;
    text-transform: uppercase;
  }

  h1 {
    padding-top: 10rem;
  }

  h2 {
    padding: 5rem 0 2rem;
  }

  select {
    appearance: none;
    padding: 0 0.5rem;
  }

  select:hover {
    cursor: pointer;
  }

  span {
    font-size: 3rem;
    padding: 0.5rem;
    border: 5px solid #5f77e6;
    border-radius: 4px;
  }
  .container {
    background-color: #b3eeee;
    height: 97vh;
  }
  .container__area {
    display: flex;
    justify-content: center;
    margin-top: 5rem;
  }

  .container__operando {
    font-size: 1.5rem;
  }

  .operador {
    font-size: 2rem;
    margin: 0 2rem 0;
  }

  .operador__select {
    font-size: 2rem;
    font-weight: bold;
  }

</style>

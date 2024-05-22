<script setup>
import { reactive } from 'vue';


const estado = reactive({
  numero1: 0,
  numero2: 0,
  filtro: '+',
})

function calcular() {
  const { filtro, numero1, numero2 } = estado;

  switch (filtro) {
    case '+':
      return parseFloat(numero1) + parseFloat(numero2);

    case '-':
      return numero1 - numero2;
    case '/':
      return  numero1 || numero2 !== 0? numero1 / numero2 : ':(';
    case 'x':
      return numero1 * numero2;
    default:
    return 'Error'
  }
}

</script>

<template>
  <div class="container text-center">
    <h1 class="mt-4">Calculadora aritmética</h1>
    <div class="row justify-content-center">
      <div class="col-3">
        <input v-model.number="estado.numero1" @keyup="evento => estado.numero1 = evento.target.value"
          class="form-control" type="number" placeholder="Digite um número" >
      </div>
      <div class="col-1">
        <select class="form-control" >
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="/">/</option>
          <option value="x">x</option>
        </select>
      </div>
      <div class="col-3">
        <input v-model.number="estado.numero2" @keyup="evento => estado.numero2 = evento.target.value"
          class="form-control" type="number" placeholder="Digite um número">
      </div>

    </div>
    <h2 class="mt-4">{{ calcular() }}</h2>
  </div>
</template>

<style scoped></style>

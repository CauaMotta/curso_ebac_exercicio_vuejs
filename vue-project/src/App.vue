<script setup>
import { reactive } from 'vue';
import Calculator from './components/Calculator.vue';

const data = reactive({
  operation: 'plus',
})
</script>

<template>
  <div class="container mt-5">
    <h1 class="text-center mb-5">Calculadora Aritmética</h1>
    <hr>
    <div class="d-flex align-items-center justify-content-center gap-3 mt-5">
      <select v-model="data.operation" class="form-select w-25" aria-label="Default select example">
        <option value="plus">Somar</option>
        <option value="minus">Subtrair</option>
        <option value="divide">Dividir</option>
        <option value="multiply">Multiplicar</option>
      </select>
      <Calculator :operation="data.operation" />
    </div>
  </div>
</template>

<style scoped></style>

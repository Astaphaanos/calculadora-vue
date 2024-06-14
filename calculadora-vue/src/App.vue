<script setup>
import { ref, computed } from 'vue'

const number1 = ref(0)
const number2 = ref(0)
const operacao = ref('somar')

const resultado = computed(() => {
  switch (operacao.value) {
    case 'somar':
      return number1.value + number2.value
    case 'subtrair':
      return number1.value - number2.value
    case 'multiplicar':
      return number1.value * number2.value
    case 'dividir':
      return number2.value !== 0 ? number1.value / number2.value : 'Erro: Divisão por zero'
    default:
      return 0
  }
})
</script>

<template> 
  <div id="calculadora" class="container mt-5 bg-light">
    <!--Header-->
    <header class="bg-dark text-white">
      <h1 class="text-center p-3">Calculadora Aritmética</h1>
    </header>

    <div class="row justify-content-center mt-4 p-4">
      <div class="col-md-3">
        <!--Primeiro input-->
        <input type="number" class="form-control" v-model.number="number1" placeholder="Número 1"/>
      </div>

      <!--Seletor de operação-->
      <div class="col-md-2">
        <select class="form-control" v-model="operacao">
          <option value="somar">+</option>
          <option value="subtrair">-</option>
          <option value="multiplicar">*</option>
          <option value="dividir">/</option>
        </select>
      </div>
      <div class="col-md-3">
        <!--Segundo input-->
        <input type="number" class="form-control" v-model.number="number2" placeholder="Número 2">
      </div>
    </div>
    <div class="row justify-content-center mt-4 bg-success text-white">
      <!--Resultado-->
      <h2 class="col-md-8 text-center p-2">
        Resultado: {{ resultado }}
      </h2>
    </div>
  </div>
</template>

<style>
#calculadora {
  font-family: Arial, sans-serif;
}

input, select {
  margin: 5px;
  padding: 10px;
  font-size: 18px;
}
</style>
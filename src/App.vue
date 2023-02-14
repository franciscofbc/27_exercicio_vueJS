<script setup>

import { reactive } from 'vue';

const estado = reactive({

  numeroA: 0,
  numeroB: 0,
  operacao: 'somar',
  resultado: 0,

})

function calcular() {
  if (estado.numeroA != '' && estado.numeroB != '') {
    switch (estado.operacao) {
      case 'somar':
        return somar()
      case 'subtrair':
        return subtrair()
      case 'multiplicar':
        return multiplicar()
      case 'dividir':
        return dividir()
    }
  } else {
    estado.resultado = 0
  }
}

function campoA(e) {
  estado.numeroA = e.target.value
  calcular()
}

function campoB(e) {
  estado.numeroB = e.target.value
  calcular()
}

function pegarOperacao(e) {
  estado.operacao = e.target.value
  calcular()
}

function somar() {
  estado.resultado = parseInt(estado.numeroA) + parseInt(estado.numeroB)
}

function subtrair() {
  estado.resultado = parseInt(estado.numeroA) - parseInt(estado.numeroB)
}

function multiplicar() {
  estado.resultado = parseInt(estado.numeroA) * parseInt(estado.numeroB)
}

function dividir() {
  estado.resultado = parseInt(estado.numeroA) / parseInt(estado.numeroB)
}

</script>

<template>
  <div class="container">
    <h1>Arithmetic calculator</h1>

    <form>
      <div class="row">
        <div class="col-4">
          <input required type="number" placeholder="Type a number" class="form-control mt-3" @keyup="campoA">
          <input required type="number" placeholder="Type a number" class="form-control mt-3" @keyup="campoB">
        </div>
      </div>
      <div class="row mt-3">
        <div class="col-3">
          <label>Select the arithmetic operation:</label>
        </div>
        <div class="col-1">
          <select class="form-control" @change="pegarOperacao">
            <option value="somar">+</option>
            <option value="subtrair">-</option>
            <option value="multiplicar">*</option>
            <option value="dividir">/</option>
          </select>
        </div>
      </div>
    </form>

    <p>Calculating...</p>
    <p>{{ estado.resultado }}</p>

  </div>

</template>

<style scoped>

</style>

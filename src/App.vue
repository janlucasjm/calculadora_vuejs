<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    numero1: 0,
    numero2: 0,
    operacoes: 'selecione',
  })

  const numero1 = (evento) => {
    estado.numero1 = evento.target.value;
  }

  const numero2 = (evento) => {
    estado.numero2 = evento.target.value;
  }

  function getOperacoes() {
    const { operacoes, numero1, numero2 } = estado;
    const valor1 = Number(numero1);
    const valor2 = Number(numero2);

    switch(operacoes) {
      case 'soma':
        return valor1 + valor2;

      case 'subtracao':
        return valor1 - valor2;

      case 'multiplicacao':
        return valor1 * valor2;

      case 'divisao':
        if (valor2 == 0){
          return 'Não é possível dividir por zero'
        } else {
          return valor1 / valor2;
        }
    }
  }

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-primary rounded-2 text-light text-center">
      <h1>Calculadora aritmética</h1>
    </header>

    <form class="py-5 ps-4 bg-body-secondary rounded-2">
      <div class="row">
        <div class="col-md-2">
          <input @keyup="numero1" class="form-control" type="number" placeholder="Digite o primeiro número">
        </div>
        <div class="col-md-2">
          <input @keyup="numero2" type="number" class="form-control" placeholder="Digite o segundo número">
        </div>
        <div class="col-md-3">
          <select @change="evento => estado.operacoes = evento.target.value" class="form-control">
            <option value="selecione" disabled selected>Selecione a operação:</option>
            <option value="soma">Soma</option>
            <option value="subtracao">Subtração</option>
            <option value="multiplicacao">Multiplicação</option>
            <option value="divisao">Divisão</option>
          </select>
        </div>
        <div class="col-md-4 d-flex align-items-center fs-4 fw-bold">
          <span>Resultado: {{ getOperacoes() }}</span>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>

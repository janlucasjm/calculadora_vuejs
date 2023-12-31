<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';

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
    <Cabecalho />
    <Formulario :primeiro-numero="numero1" :segundo-numero="numero2" :seleciona-lista="evento => estado.operacoes = evento.target.value" :get-operacoes="getOperacoes()"/>
  </div>
</template>

<style scoped>

</style>

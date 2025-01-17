<script setup>
  import { reactive } from 'vue';
  import Calculadora from './components/Calculadora.vue';

  const estado = reactive({
    numero1: '',
    numero2: '',
    operacao: '+',
    resultado: '',
  });


  const getResultado = () => {
    const num1 = parseFloat(estado.numero1);
    const num2 = parseFloat(estado.numero2);

    if (isNaN(num1) || isNaN(num2)) {
      return "Erro: Números inválidos";
    }

    switch (operacao) {
      case '+':
        return num1 + num2;
      case '-':
        return num1 - num2;
      case '*':
        return num1 * num2;
      case '/':
        return num2 !== 0 ? num1 / num2 : "Erro: Divisão por zero";
      default:
        return "Operação inválida";
    }
  }

</script>

<template>
  <div class="container">
    <Calculadora :primero-numero="estado.numero1" :trocar-operacao="estado.operacao" :segundo-numero="estado.numero2" :resultado-numero="getResultado()" />
    
  </div>
</template>

<style scoped>

</style>

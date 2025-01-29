<script setup>
  import { reactive, watch } from 'vue';
  import Calculadora from './components/Calculadora.vue';
  

  const estado = reactive({
    num1: '',
    num2: '',
    operacao: '+',
    resultado: null,
  });

  const calcularResultado = () => {
    const num1 = parseFloat(estado.num1);
    const num2 = parseFloat(estado.num2);

    if (isNaN(num1) || isNaN(num2)) {
      estado.resultado = null; 
      return;
    }

    switch (estado.operacao) {
      case '+':
        estado.resultado = num1 + num2;
        break;
      case '-':
        estado.resultado = num1 - num2;
        break;
      case '*':
        estado.resultado = num1 * num2;
        break;
      case '/':
        estado.resultado = num2 !== 0 ? num1 / num2 : "Erro: Divisão por zero";
        break;
      default:
        estado.resultado = "Operação inválida";
      }
    };

  watch(
    () => [estado.num1, estado.num2, estado.operacao],
    calcularResultado
  );

</script>

<template>
  <div class="container">
    <Calculadora :primero-numero="estado.num1" :operacao="estado.operacao" :segundo-numero="estado.num2" :resultado="estado.resultado" @update:primeiro-numero="estado.num1 = $event" @update:operacao="estado.operacao = $event" @update:segundo-numero="estado.num2 = $event" />
  </div>
</template>

<style scoped>

</style>

<script setup>
  import { computed, reactive, watch } from 'vue';
  import Calculadora from './components/Calculadora.vue';
  

  const estado = reactive({
    num1: "",
    num2: "",
    mudaOperacao: "+",
  });

  const calcularResultado = computed(() => {
    const num1 = parseFloat(estado.num1);
    const num2 = parseFloat(estado.num2);

    if (isNaN(num1) || isNaN(num2)) {
      return null
    }

    switch (estado.mudaOperacao) {
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
    });

</script>

<template>
  <div class="container">
    <Calculadora :primeiroNumero="estado.num1" :mudaOperacao="estado.mudaOperacao" :segundoNumero="estado.num2" :novoResultado="calcularResultado" @update:primeiroNumero="estado.num1 = $event" @update:mudaOperacao="estado.mudaOperacao = $event" @update:segundoNumero="estado.num2 = $event" />
  </div>
</template>

<style scoped>

</style>

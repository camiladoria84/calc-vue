<script setup>
  const props = defineProps({ primeiroNumero: [String, Number], mudaOperacao: String, segundoNumero: [String, Number], novoResultado: [Number, String]});
  const emit = defineEmits(['update:primeiroNumero', 'update:mudaOperacao', 'update:segundoNumero']);
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-dark rounded-7 text-white" >
      <h2>Calculadora Aritimética</h2>
      <p>Faça o seu cálculo:</p>
  </header>
  <form @submit.prevent>
    <div class="row">
      <div class="col-2">
        <input id="num1" :value="props.primeiroNumero" @input="emit('update:primeiroNumero', $event.target.value)" required type="number" placeholder="número 1" class="form-control" />
      </div>
      <div class="col-1">
        <select id="operacao" :value="props.mudaOperacao" @change="emit('update:mudaOperacao', $event.target.value)" class="form-control text-center">
          <option value="+" >+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-2">
        <input id="num2" :value="props.segundoNumero" @input="emit('update:segundoNumero', $event.target.value)" required type="number" placeholder="número 2" class="form-control" @blur="emit('update:calcular')" />
        </div>
      <div class="col-1">
        <input id="igual" readonly class="form-control text-center" placeholder="="/>
      </div>
      <div class="col-2" >
        <input id="resultado"  readonly placeholder="Resultado" type="text" class="form-control" :value="props.novoResultado"  />
      </div>
    </div>
  </form>
</template>

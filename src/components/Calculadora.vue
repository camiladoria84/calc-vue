<script setup>
  const props = defineProps({ primeroNumero: [String, Number], operacao: String, segundoNumero: [String, Number], resultado: [Number, String]});
  const emit = defineEmits(['update:primero-numero', 'update:operacao', 'update:segundo-numero', 'calcular-resultado']);
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-dark rounded-7 text-white" >
      <h2>Calculadora Aritimética</h2>
      <p>
        Faça o seu cáculo:
      </p>
  </header>
  <form @submit.prevent>
    <div class="row">
      <div class="col-2">
        <input id="num1" :value="props.primeroNumero" @input="emit('update:primero-numero', $event.target.value)" required type="number" placeholder="número 1" class="form-control" />
      </div>
      <div class="col-1">
        <select id="operacao" :value="props.operacao" @change="emit('update:operacao', $event.target.value)" class="form-control text-center">
          <option value="+" >+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-2">
        <input id="num2" :value="props.segundoNumero" @input="emit('update:segundo-numero', $event.target.value)" required type="number" placeholder="número 2" class="form-control" />
      </div>
      <div class="col-1">
        <label class="form-control text-center">=</label>
      </div>
      <div class="col-2" >
        <input readonly placeholder="Resultado" type="text" class="form-control" :value="props.resultado" />
        <p v-if="props.resultado !== null" class="form-control">Resultado: {{ props.resultado }}</p>
        <p v-else> Digite números válidos e selecione a operação.</p>
      </div>
    </div>
  </form>
</template>

<script setup>
  const props = defineProps(['primeroNumero', 'trocarOperacao', 'segundoNumero', 'resultadoNumero'])
</script>

<template>
  <header class="p-5 mb-4 mt-4 bg-dark rounded-7 text-white">
      <h2>Calculadora Aritimética</h2>
      <p>
        Faça o seu cáculo
      </p>
    </header>
    <form>
    <div class="row">
      <div class="col-2">
        <input @change="props.primeroNumero" required type="number" placeholder="primeiro número" class="form-control">
      </div>
      <div class="col-1">
        <select @change="props.trocarOperacao" class="form-control text-center">
          <option value="+" >+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-2">
        <input @change="props.segundoNumero" required type="number" placeholder="segundo número" class="form-control" >
      </div>
      <div class="col-1">
        <label class="form-control text-center">=</label>
      </div>
      <div class="col-2" >
        <input :value="props.resultadoNumero" readonly placeholder="resultado" class="form-control" />
      </div>
    </div>
  </form>
</template>

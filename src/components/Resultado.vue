<script setup>
const props = defineProps(['resultadosOperacao','dividindoPorZero'])
</script>
<template>
    <h4 v-if="props.resultadosOperacao !== null" class="text-center fw-normal mt-3">Resultado: {{ props.resultadosOperacao }}</h4>
    <h4 v-if="props.dividindoPorZero === true" class="text-center fw-normal mt-3">Não é possível dividir por zero!</h4>
</template>
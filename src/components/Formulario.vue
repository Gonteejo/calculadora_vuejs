<script setup>
const props = defineProps(['trocaNumero1', 'trocaOperador', 'trocaNumero2']);
</script>
<template>
    <form class="row">
        <input @keyup="props.trocaNumero1" type="number" class="col-md-4 mx-1">
        <select @change="props.trocaOperador" id="operador" name="operador" class="col-md-2 mx-1">
            <option value="+" selected>+</option>
            <option value="-">-</option>
            <option value="*">x</option>
            <option value="/">÷</option>
        </select>
        <input @keyup="props.trocaNumero2" type="number" class="col-md-4 mx-1">
    </form>
</template>
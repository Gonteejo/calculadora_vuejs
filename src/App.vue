<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue'
import Formulario from './components/Formulario.vue'
import Resultado from './components/Resultado.vue'

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operador: '+',
  resultado: null,
  dividindoPorZero: false,
});

function trocaOperador(evento) {
  estado.operador = evento.target.value;
  estado.resultado = realizarOperacao();
}

function trocaNumero1(evento) {
  estado.numero1 = Number(evento.target.value);
  estado.resultado = realizarOperacao();
}

function trocaNumero2(evento) {
  estado.numero2 = Number(evento.target.value);
  estado.resultado = realizarOperacao();
}

function realizarOperacao() {
  switch (estado.operador) {
    case '+':
      return estado.numero1 + estado.numero2;
    case '-':
      return estado.numero1 - estado.numero2;
    case '*':
      return estado.numero1 * estado.numero2;
    case '/':
      if (estado.numero2 === 0) {
        estado.dividindoPorZero = true;
        return null
      }
      else {
        estado.dividindoPorZero = false;
        return estado.numero1 / estado.numero2;
      }
  }
}
</script>

<template>
  <div class="body d-flex align-items-center py-4 bg-body-tertiary">
    <div class="form-container m-auto">
      <Cabecalho />
      <Formulario :troca-numero1="trocaNumero1" :troca-numero2="trocaNumero2" :troca-operador="trocaOperador" />
      <Resultado :resultados-operacao="estado.resultado" :dividindo-por-zero="estado.dividindoPorZero" />
    </div>
  </div>
</template>

<style scoped>
.body {
  height: 100vh;
}

.form-container {
  max-width: 400px;
  padding: 1rem;
}
</style>

<script setup>
import { reactive, computed } from 'vue';


const estado = reactive ({
  numero1: 0,
  numero2: 0,
  operacao: 'adicao',
})

const resultado = computed (() => {
  const n1 = parseFloat(estado.numero1);
  const n2 = parseFloat(estado.numero2);

  switch (estado.operacao) {
    case 'adicao':
      return n1 + n2;
    case 'subtracao':
      return n1 - n2;
    case 'multiplicacao':
      return n1 * n2;
    case 'divisao':
      return n1 / n2;
    default:
      return 0;
  }
})
</script>

<template>
  <div class="container">

    <div class="campos">
      <div class="campos-pnumero">
        <input type="number" v-model="estado.numero1" placeholder="Adicione o número">
      </div>
      <div class="campos-selecao">
        <select v-model="estado.operacao">
          <option value="multiplicacao">Multiplicar ×</option>
          <option value="divisao">Dividir ÷</option>
          <option value="adicao">Somar +</option>
          <option value="subtracao">Subtrair -</option>
        </select>
      </div>
      <div class="campos-snumero">
        <input type="number" v-model="estado.numero2" placeholder="Adicione o número">
      </div>
    </div>

    <div class="resultado">
      <h4>Resultado: {{ resultado }}</h4>
    </div>
  </div>
</template>

<style scoped>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .container {
    width: 100%;
    max-width: 300px;
    height: 95vh;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }

  .campos {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .campos input, .campos select {
    width: 100%;
    height: 30px;
    text-align: right;
  }
</style>
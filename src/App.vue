<script setup>
import { computed, reactive, ref } from 'vue';
import FormView from '@/components/FormView.vue';
import DadosView from '@/components/DadosView.vue';

const dados = ref('')

function save(item) {
  console.log(item)
  dados.value = item
}

const mostrarDados = computed(() => {
  return dados.value !== ''
})

</script>

<template>
  <div>
    <FormView @salvar="save" />
  </div>
  <div>
    <DadosView v-if="mostrarDados" :Dados="dados" />
  </div>
</template>

<style scoped>
div{
  margin: 0 50px;
}
</style>

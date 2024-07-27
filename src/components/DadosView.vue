<script setup>
import { reactive } from 'vue'
const props = defineProps({
    Dados: {
        type: Object,
        required: true
    }
})

console.log(props.Dados)

</script>
<template>
    <div class="resultado">
        <div class="mainResultados">
            <h1>Resultado</h1>
            <p>Nome: {{ props.Dados.nome }}</p>
            <p>Nascimento: {{ props.Dados.nascimento }}</p>
            <p>Email: {{ props.Dados.email }}</p>
            <p>Cidade: {{ props.Dados.cidade }}</p>
            <p>Estado: {{ props.Dados.estado }}</p>
            <p>Hobbies: {{ props.Dados.hobbies }}</p>
            <p>Linguagem Preferida: {{ props.Dados.linguagemProg }}</p>
            <div class="mainResultados">
                <p> Biografia: {{ props.Dados.biografia }}</p>
            </div>
        </div>
    </div>
</template>
<style scoped>
.resultado {
    background-color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 50px;
    border-radius: 20px;
    gap: 40px;
    border: 1.5px solid #0d0d0d;
    color: #0d0d0d;
    animation: spin 2s ease;
    animation-iteration-count: 1;
}

.resultado h1 {
    font-size: 50px;
    border-bottom: 1px solid #0d0d0d;
    margin: 0 0 10px 0;
}

.resultado .mainResultados{
     background-color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
}

@keyframes spin {
    to {
        transform: translateX(0px);
    }

    from {
        transform: translateX(2000px);
    }
}
</style>

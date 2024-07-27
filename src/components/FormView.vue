<script setup>
import { ref, computed, reactive } from 'vue'

const emit = defineEmits(['save'])

const pessoa = reactive({
    nome: '',
    senha: '',
    confSenha: '',
    nascimento: '',
    email: '',
    cep: '',
    cidade: '',
    estado: '',
    hobbies: [],
    linguagemProg: '',
    biografia: ''
});

const ListaEstados = [
    { sigla: 'AC', nome: 'Acre' },
    { sigla: 'AL', nome: 'Alagoas' },
    { sigla: 'AP', nome: 'Amapá' },
    { sigla: 'AM', nome: 'Amazonas' },
    { sigla: 'BA', nome: 'Bahia' },
    { sigla: 'CE', nome: 'Ceará' },
    { sigla: 'DF', nome: 'Distrito Federal' },
    { sigla: 'ES', nome: 'Espírito Santo' },
    { sigla: 'GO', nome: 'Goiás' },
    { sigla: 'MA', nome: 'Maranhão' },
    { sigla: 'MT', nome: 'Mato Grosso' },
    { sigla: 'MS', nome: 'Mato Grosso do Sul' },
    { sigla: 'MG', nome: 'Minas Gerais' },
    { sigla: 'PA', nome: 'Pará' },
    { sigla: 'PB', nome: 'Paraíba' },
    { sigla: 'PR', nome: 'Paraná' },
    { sigla: 'PE', nome: 'Pernambuco' },
    { sigla: 'PI', nome: 'Piauí' },
    { sigla: 'RJ', nome: 'Rio de Janeiro' },
    { sigla: 'RN', nome: 'Rio Grande do Norte' },
    { sigla: 'RS', nome: 'Rio Grande do Sul' },
    { sigla: 'RO', nome: 'Rondônia' },
    { sigla: 'RR', nome: 'Roraima' },
    { sigla: 'SC', nome: 'Santa Catarina' },
    { sigla: 'SP', nome: 'São Paulo' },
    { sigla: 'SE', nome: 'Sergipe' },
    { sigla: 'TO', nome: 'Tocantins' }
]
const button = ref(false)

const nomeBotao = computed(() => {
    return button.value ? 'Esconder' : 'Mostrar';
});

function enviar(dados) {

    emit('salvar', dados)
}

</script>
<template>
    <main class="formulario">
        <form @submit.prevent="">
            <h1>Formulário</h1>
            <div class="input">
                <label for="nome">Nome</label>
                <input type="text" v-model.trim="pessoa.nome" placeholder="Digite seu nome" id="inputNome" required />
            </div>
            <div class="input">
                <label for="Email">Email</label>
                <input id="Email" type="email" v-model.trim="pessoa.email" placeholder="Digite seu email" required>
            </div>
            <div class="input">
                <label for="Senha">Senha</label>
                <input id="Senha" type="password" v-model.trim="pessoa.senha" placeholder="Digite sua Senha" required>
            </div>
            <div class="input">
                <label for="ConSenha">Confirmar Senha</label>
                <input id="ConSenha" type="password" v-model.trim="pessoa.confSenha" placeholder="Confirme sua Senha"
                    required>
            </div>
            <div class="input">
                <label for="nascimento">Nascimento</label>
                <input id="nascimento" type="date" v-model="pessoa.nascimento" placeholder="Digite sua Nascimento "
                    required>
            </div>
            <div class="input">
                <label for="cep">CEP</label>
                <input id="cep" type="number" v-model="pessoa.cep" placeholder="Digite seu CEP" required>
            </div>
            <div class="input">
                <label for="inputCidade">Cidade</label>
                <input id="inputCidade" type="text" v-model="pessoa.cidade" placeholder="Digite sua Cidade" required>
            </div>
            <div class="input">
                <label for="Estado">Estado</label>

                <select id="Estado" value="Estado" v-model="pessoa.estado" required>
                    <option v-for="Estado of ListaEstados" :key="Estado.sigla" :value="Estado.sigla">
                        {{ Estado.nome }}
                    </option>
                </select>
            </div>
            <div class="checkbox">
                <p class="titulo">Hobbies:</p>
                <input type="checkbox" id="esportes" value="Esporte" v-model="pessoa.hobbies">
                <label for="esportes">Esportes</label>

                <input type="checkbox" id="viagens" value="Viagens" v-model="pessoa.hobbies">
                <label for="viagens">Viagens</label>

                <input type="checkbox" id="musicas" value="Música" v-model="pessoa.hobbies">
                <label for="musicas">Músicas</label>

                <input type="checkbox" id="leitura" value="Leitura" v-model="pessoa.hobbies">
                <label for="leitura">Leitura</label>

                <input type="checkbox" id="videogame" value="VIdeoGame" v-model="pessoa.hobbies">
                <label for="videogame">Video Game</label>
            </div>
            <div class="checkbox">
                <p class="titulo">Linguagem preferida:</p>
                <input type="radio" id="Js" value="JavaScript" v-model="pessoa.linguagemProg">
                <label for="Js">JavaScript</label>

                <input type="radio" id="Java" value="Java" v-model="pessoa.linguagemProg">
                <label for="Java">Java</label>

                <input type="radio" id="C" value="C" v-model="pessoa.linguagemProg">
                <label for="C">C</label>

                <input type="radio" id="Py" value="Python" v-model="pessoa.linguagemProg">
                <label for="Py">Python</label>

                <input type="radio" id="C#" value="C#" v-model="pessoa.LinguagemProg">
                <label for="C#">C#</label>
            </div>
            <div class="input">
                <label for="bio">Biografia</label>
                <textarea type="text" id="bio" placeholder="Sua Biografia" v-model="pessoa.biografia"></textarea>
            </div>
            <div class="button">
                <button @click="enviar(pessoa)" type="submit">{{ nomeBotao }}</button>
            </div>
        </form>
    </main>
</template>
<style scoped>
* {
    padding: 0;
    margin: 0;
    border: 0;
    box-sizing: border-box;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

.formulario {
    background-color: #0d0d0d;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 50px;
    border-radius: 20px;
    color: #fff;
}

form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    gap: 7px;
}

.formulario form h1 {
    font-size: 50px;
    border-bottom: 1px solid #fff;
    margin: 0 0 10px 0;
}

.formulario form .input {
    display: flex;
    justify-content: start;
    align-items: center;
    gap: 15px;
}

.formulario form .input input {
    padding: 2.5px;
    border-radius: 7px;
}

.formulario form .button {
    display: flex;
    justify-content: end;
    align-items: center;
}

.formulario form .button button {
    padding: 5px;
    border-radius: 10px;
}

.formulario form .checkbox{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
}
</style>
<template>
    <div>
        <form @submit.prevent="salvar">
            <h2>Cadastro Jogador</h2>
            Nome Jogador: 
            <input type="text" v-model="jogador.nome" required autofocus>

            <br>

            Salario Jogador:
            <input type="text" v-model="jogador.salario" required>

            <br>

            Posição que vai jogar:
            <input type="text" v-model="jogador.posicao" required>

            <br>

            Time:
            <select v-model="jogador.time" @click="buscarTimes">
                <option v-for="t in times" :key="t.id" :value="t">
                    {{ t.nome }}
                </option>
            </select>
            <input type="submit"/>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            jogador: {
                nome: '',
                salario: null,
                posicao: ''
            },
            times: [],
        }
    },
    methods: {
         salvar(){
            axios.post("http://localhost:8080/jogador", this.jogador).then(response =>{
                this.jogador = response.data
                alert('Jogador cadastrado!')
                this.jogador.id = null
                this.jogador.nome = ''
                this.jogador.salario = null
                this.jogador.posicao = ''   
            }).catch(erro =>{
                alert(erro.response)
            })
        },
        buscarTimes(){
            axios.get("http://localhost:8080/time").then(response => {
                this.times = response.data
        })
        }
    }
}
</script>

<style>

</style>
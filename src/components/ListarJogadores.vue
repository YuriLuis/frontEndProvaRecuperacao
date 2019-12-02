<template>
    <div>
        <h2>Lista de Jogadores</h2>
        <button @click="listaJogadores">Ver todos Times</button>
        <button @click="fechar">Fechar</button>
        <table v-if="jogadores != null ">
            <tr>
                <th>Nome</th>
                <th>Salario</th>
                <th>Posição</th>
                <th>Time</th>
            </tr>
            <tr v-for="j in jogadores" :key="j.id">
                <td>{{ j.nome}}</td>
                <td>{{ j.salario}}</td>
                <td>{{ j.posicao}}</td>
                <td>{{ j.time.nome}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            jogadores: []
        }
    },
    methods: {
        listaJogadores(){
            axios.get("http://localhost:8080/jogador").then(response => {
                this.jogadores = response.data
            })
        },
        fechar(){
            return this.jogadores = null
        }
    }
}
</script>

<style>
tr {
    margin: 20px
}

</style>
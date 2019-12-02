<template>

    <div>
        <h2>Lista de Times</h2>
        <button @click="listaTimes">Ver todos Times</button>
        <button @click="fechar">Fechar</button>
        <table v-if="times != null ">
            <tr>
                <th>Nome Time</th>
            </tr>
            <tr v-for="t in times" :key="t.id">
                <td>{{ t.nome}}</td>
            </tr>

        </table>
    </div>
  
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            times: []
        }
    },
    methods: {
        listaTimes(){
            axios.get("http://localhost:8080/time").then(response => {
                this.times = response.data
            })
        },
        fechar(){
            return this.times = null
        }
    }
}
</script>

<style>
tr {
    margin: 10px
}
</style>
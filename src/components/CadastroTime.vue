<template>
    <div>
        <form @submit.prevent="salvar">

            <h2>Cadastro Do time</h2>
            Nome do Time:
            <input type="text" v-model="time.nome" autofocus required> <br>

             <input type="submit"/>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            time: {
                nome: ''
            }
        }
    }, 
    methods: {
        salvar(){
            axios.post(" http://localhost:8080/time", this.time).then(response => {
                this.time = response.data
                alert('Time Cadastrado!')
                this.time.id = null
                this.time.nome = ''
            }).catch(error => {
                alert(error.response)
            })
        }
    }
}
</script>

<style>

</style>
<template>
  <div id="app">
  <cadastro-time></cadastro-time>
  <lista-times></lista-times>
  <hr>
  <cadastro-jogador></cadastro-jogador>
  <lista-jogadores></lista-jogadores>
  <hr>
  </div>
</template>

<script>
import CadastroTime from './components/CadastroTime'
import CadastroJogador from './components/CadastroJogador'
import ListaTimes from './components/ListaTimes'
import ListaJogadores from './components/ListarJogadores'

export default {
  name: 'app',
  components: {
    CadastroTime, CadastroJogador,
    ListaTimes, ListaJogadores
  }
}
</script>

<style>

</style>

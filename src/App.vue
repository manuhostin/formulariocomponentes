<script setup>
import { reactive } from 'vue'
import RegistroB from './components/RegistroB.vue'
import RegistroA from './components/RegistroA.vue'

const usuario = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmarsenha: '',
  datadenascimento: '',
  endereco: '',
  cidade: '',
  estado: '',
  hobby: [],
  linguagens: '',
  biografia: ''
})

function salvar(novoResultado) {
  Object.assign(usuario, novoResultado)
}
</script>

<template>
  <RegistroA @resultado="salvar" />
  <RegistroB :usuario="usuario" />
</template>

<style scoped></style>

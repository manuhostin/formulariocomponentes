<script setup>
import { reactive, ref } from 'vue'
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
const estados = [
  { uf: 'AC', name: 'Acre' },
  { uf: 'AL', name: 'Alagoas' },
  { uf: 'AP', name: 'Amapá' },
  { uf: 'AM', name: 'Amazonas' },
  { uf: 'BA', name: 'Bahia' },
  { uf: 'CE', name: 'Ceará' },
  { uf: 'DF', name: 'Distrito Federal' },
  { uf: 'ES', name: 'Espírito Santo' },
  { uf: 'GO', name: 'Goiás' },
  { uf: 'MA', name: 'Maranhão' },
  { uf: 'MT', name: 'Mato Grosso' },
  { uf: 'MS', name: 'Mato Grosso do Sul' },
  { uf: 'MG', name: 'Minas Gerais' },
  { uf: 'PA', name: 'Pará' },
  { uf: 'PB', name: 'Paraíba' },
  { uf: 'PR', name: 'Paraná' },
  { uf: 'PE', name: 'Pernambuco' },
  { uf: 'PI', name: 'Piauí' },
  { uf: 'RJ', name: 'Rio de Janeiro' },
  { uf: 'RN', name: 'Rio Grande do Norte' },
  { uf: 'RS', name: 'Rio Grande do Sul' },
  { uf: 'RO', name: 'Rondônia' },
  { uf: 'RR', name: 'Roraima' },
  { uf: 'SC', name: 'Santa Catarina' },
  { uf: 'SP', name: 'São Paulo' },
  { uf: 'SE', name: 'Sergipe' },
  { uf: 'TO', name: 'Tocantins' }
]
const mostrarResultado = ref(false)
function validar() {
  let erro = false
  if (usuario.senha !== usuario.confirmarsenha) {
    alert('Senhas não batem')
    erro = true
  }
  if (!erro) {
    mostrarResultado.value = !mostrarResultado.value
  }
}
</script>

<template>
  <div class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <form @submit.prevent="validar">
        <div class="row">
          <label for="">Nome:</label>
          <input type="text" v-model="usuario.nome" required />
        </div>
        <div class="row">
          <label for="">Email:</label>
          <input type="email" v-model="usuario.email" />
        </div>
        <div class="row">
          <label for="">Senha:</label>
          <input type="password" v-model="usuario.senha" />
        </div>
        <div class="row">
          <label for="">Confirmar Senha:</label>
          <input type="password" v-model="confirmarsenusuario.ha" />
        </div>
        <div class="row">
          <label for="">Data de Nascimento:</label>
          <input type="date" v-model="usuario.datadenascimento" required />
        </div>
        <div class="row">
          <label for="">Endereço:</label>
          <input type="text" v-model="usuario.endereco" required />
        </div>
        <div class="row">
          <label for="">Cidade:</label>
          <input type="text" v-model="usuario.cidade" required />
        </div>
        <div class="row">
          <label for="">Estado:</label>
          <select v-model="usuario.estado" required>
            <option selected disabled value="">Selecionar...</option>
            <option v-for="estado of estados" :key="estado.uf" :value="estado.uf">
              {{ estado.name }}
            </option>
          </select>
        </div>
        <div class="row">
          <p>Linguagem:</p>
          <div class="language-options">
            <input type="radio" id="java" value="java" v-model="usuario.linguagens" />
            <label for="java">Java</label>

            <input type="radio" id="js" value="js" v-model="usuario.linguagens" />
            <label for="js">JavaScript</label>

            <input type="radio" id="c" value="c" v-model="usuario.linguagens" />
            <label for="c">C</label>

            <input type="radio" id="python" value="python" v-model="usuario.linguagens" />
            <label for="python">Python</label>
          </div>
        </div>
        <div clas="row">
          <label for=""> Hobbies </label>
          <input type="checkbox" id="jogos" value="jogos" v-model="usuario.hobby" />
          <label for="jogos">Jogos</label>
          <input type="checkbox" id="artes" value="artes" v-model="usuario.hobby" />
          <label for="artes">Artes</label>
          <input type="checkbox" id="musica" value="musica" v-model="usuario.hobby" />
          <label for="musica">Música</label>
        </div>
        <div class="row">
          <label for=""> Biografia: </label>
          <textarea v-model="usuario.biografia"></textarea>
        </div>
        <button type="submit">Mostrar</button>
      </form>
    </div>
    <div>
      <h1>teste</h1>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

* {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
}

.language-options {
  display: flex;
  flex-wrap: wrap;
}

.language-options input[type='radio'] {
  margin-right: 10px;
}

.language-options label {
  margin-right: 20px;
}
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.formulario {
  background-color: #ff67e6;
  padding: 20px;
  margin-bottom: 20px;
}

.formulario h1 {
  text-align: center;
  color: #9e0162;
}

.formulario form .row {
  margin-bottom: 15px;
}

.formulario form .row label {
  display: block;
  margin-bottom: 5px;
}

.formulario form .row input[type='text'],
.formulario form .row input[type='email'],
.formulario form .row input[type='password'],
.formulario form .row input[type='date'],
.formulario form .row select,
.formulario form .row textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ff97fa;
  border-radius: 4px;
  box-sizing: border-box;
}

.formulario form .row textarea {
  height: 100px;
}

.formulario form button {
  background-color: #9c0068;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.formulario form button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

.resultado {
  background-color: #f8a7ff;
  padding: 20px;
}

.resultado h1 {
  text-align: center;
  color: #a50f80;
}

.resultado p {
  margin-bottom: 10px;
}
</style>

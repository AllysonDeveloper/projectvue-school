<template>
  <div>
   <Titulo texto="Alunos"/>
   <div class="AddAluno">
     <input type="text" placeholder="Nome do Aluno" v-model="nome" v-on:keyup.enter="addAluno()">
     <button @click="addAluno()" class="btn btnInput">Adicionar</button>
   </div>
   <span class="msg_alert" v-if="vazio">Escreva o nome antes de adicionar!</span>
   <table border="2px">
     <thead>
       <th>Mat.</th>
       <th>Nome</th>
       <th>Opções</th>
     </thead>
     <tbody v-if="alunos.length">
       <tr v-for="(aluno, index) in alunos" :key="aluno.index">       
         <td>{{aluno.id}}</td>
         <td>{{aluno.nome}}</td>
        <td class="ultimaColuna"><button class="btn btn_Danger" @click="remover(aluno, index)">Remover</button></td>
       </tr>
     </tbody>
     <tfoot v-else>
       Nenhum aluno foi encontrado!
     </tfoot>
   </table>
  </div>
</template>

<script>
import Titulo from './Titulo.vue';

export default {
  name: 'Alunos',
  components: {
    Titulo
  },
  data(){
    return{
      titulo: "Aluno",
      nome: '',
      vazio: false,
      alunos: [],
    }},
    created (){
      this.$http.get('http://localhost:3000/alunos')
      .then(res => res.json())
      .then(alunos => this.alunos = alunos)
    },
    methods: {
      addAluno() {
        if(this.nome != ""){
          let _aluno = {nome: this.nome}
          this.vazio = false;
          this.$http.post('http://localhost:3000/alunos', _aluno)
          .then(res => res.json())
          .then(aluno => {
            this.alunos.push(aluno);
            this.nome="";
          })
        }else
        this.vazio = true;
      },
      remover(aluno){
        this.$http.delete(`http://localhost:3000/alunos/${aluno.id}`)
          .then(()=>{
            this.alunos = this.alunos.filter((value)=>{
            return value.id != aluno.id;
          })
        });
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

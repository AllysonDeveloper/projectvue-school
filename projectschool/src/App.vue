<template>
  <Alunos/>
</template>

<script>
import Alunos from './components/Alunos.vue'

export default {
  name: 'App',
  components: {
    Alunos
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  height: 100%;
  background-color: #eee;
  display: grid;
  justify-items: center;
}

#app{
  display: grid;
  justify-items: center;
  padding: 40px;
}

table{
  font-size: 18px;
}
thead{
  background-color: rebeccapurple;
  color: white;
}
thead th{
  padding: 5px 10px;
}
td{
  padding: 5px 10px;
}
.btn_Danger{
  background-color: rgb(247, 38, 38);
}
.btnInput{
  background-color: rgb(30, 124, 30);
}
.btn{
  padding: 10px;
  color: white;
  font-weight: bold;
  cursor: pointer;
  border: 1px solid black;
  border-radius: 10px;
  border-bottom: 3px solid black;
}
.btn:hover{
  border-bottom: 1px solid black;
  margin-top: 2px;
}
.ultimaColuna{
  text-align: center;
}
.AddAluno{
  display: flex;
  margin-bottom: 10px;
}
input{
  padding: 10px;
  margin-right: 5px;
  width: 80%;
  outline: 0;
  font-size: 18px;
}

.msg_alert{
  display: block;
  color: red;
  font-size: 18px;
  margin-bottom: 5px;
}
</style>

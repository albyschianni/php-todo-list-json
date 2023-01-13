<template>
  <h1>TO DO LIST </h1> 

  <ul>
    <li v-for="(todoElem, ind) in todoList" :key="ind">
        {{ todoElem.text }}
    </li>
  </ul>

  <form @submit="createNewTask">
    
    <input type="text" name="text" v-model="newTodoText">
    <input type="submit" value="Aggiungi">

  </form>

</template>


<script>

  const API_URL = "http://localhost:8888/";

  import axios from 'axios';

  export default{
    name: 'HelloWorld',
    data() {

      return {

        todoList: [],
        newTodoText:""

      };
    },
    methods: {
      
      getAllData() {

        axios.get(API_URL + "api.php")
          .then(res => {

            const data = res.data;

            this.todoList = data;
          });
      },
      createNewTask(e){

        e.preventDefault();

        const newTodoText = this.newTodoText;
        
        const params = {params: {

          "text": newTodoText

        }};

        axios.get(API_URL + "api_create_new_task.php", params)
          .then(res => {

            const data = res.data;

            this.newTodoText = "" ;
            this.getAllData();
          });
      }
    },
    mounted(){

      this.getAllData();
    }

  }

</script>



<style scoped>

</style>

<script>

  const API_URL = "http://localhost:8888/api.php";

  import axios from 'axios';

  export default{
    name: 'HelloWorld',
    data() {

      return {

        todoList: []
      };
    },
    methods: {
      
      forSubmit(e)  {
        e.preventDefault();
        console.log('hello World');
      }
    },
    mounted(){
      axios.get(API_URL)
        .then(res => {

          const data = res.data;

          this.todoList = data;
        });
    }
  }

</script>

<template>
  <h1>HelloWorld To Do </h1> 

  <ul>
    <li v-for="(todoElem, ind) in todoList" :key="ind">
        {{ todoElem.text }}
    </li>
  </ul>

  <form @submit="forSubmit">
    
    <input type="submit" value="Aggiungi">

  </form>



  <!-- <input type="text"> -->
</template>

<style scoped>

</style>

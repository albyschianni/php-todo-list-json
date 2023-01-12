<script>

  const API_URL = "http://localhost:8888/api.php";

  import axios from 'axios';

  export default{
    name: 'HelloWorld',
    mounted(){
      axios.get(API_URL)
        .then(res => {

          const data = res.data;

          console.log(data);
        });
    }
  }

</script>

<template>
  hello HelloWorld

</template>

<style scoped>

</style>

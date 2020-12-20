<template>
  <div class="container position-relative">
    <div >
      <input type="text" />
      <input type="password" />
      <button @click="login" class="btn btn-waring">check</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      username:null,
      pswrd:null
    };
  },
  methods:{
    login(){
      axios.get('http://localhost:3000/user')
  .then(function(res) {
    if(r){
 console.log("oldu", res.data)
  }else{
    console.log("olmadı")
  }
  
     
    
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
    }
  }
};
</script>

<style>
</style>
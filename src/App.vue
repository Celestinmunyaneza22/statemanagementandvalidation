<template>
<div>
  <center>
    <p>{{ counter }}</p>
    <button class="btn btn-primary m-3" @click="increment">Increment</button>
    <button class="btn btn-danger m-3" @click="reset">Reset</button>
    <button class="btn btn-success m-3" @click="decrement">Decrement</button><br><br>
    <p v-if="errors.length">
     <ul>
      <li v-for="error in errors" v-bind:key="error.id">
      {{ error }}
      </li>
     </ul>
    </p>
    <form action="" method="post" @submit="checkForm">
      username:<input type="text" name="username" v-model="username"><br><br>
      password:<input type="password" name="password" v-model="password"><br><br>
      <button type="submit">Send</button>
    </form>
  </center>
</div>
</template>

<script>

export default {
name:"App",
data:function(){
  return{
    errors:[],
    username:null,
    password:null,
  }
},
computed:{
  counter(){
    return this.$store.getters.counter;
  }
},
methods:{
  increment(){
    return this.$store.dispatch('increment')
  },
  reset(){
    return this.$store.dispatch('reset')
  },
  decrement(){
    return this.$store.dispatch('decrement')
  },
  checkForm(e){
    if(this.username && this.password){
      console.log("Welcome");
    }
    // this.errors=[];
    if(!this.username){
      this.errors.push("username is required")
    }
    if(!this.password){
      this.errors.push("password is required")
    }
    // console.log("errors", this.errors);
    e.preventDefault();
  }
}
}
</script>
<style scoped>
ul,li{
  list-style: none;
  color:red;
}
</style>

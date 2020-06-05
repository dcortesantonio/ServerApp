<template>
  <div id="app">
    <app-header></app-header>
    <router-link to="history" tag="button" class="btn btn-primary">History</router-link>
    <img alt="Vue logo" src="./assets/logo.png">
  </div>
</template>

<script>
  //    <button class="btn btn-primary">CLick for fun</button>
import header from "./components/header";
export default {
  name: 'app',
  components:{
          //'users':User,
   // 'home': HelloWorld,
    'app-header': header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

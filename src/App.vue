<template>
  <div>
    <h1>VUE</h1>
  </div>
  <fieldset>
    <legend>Methods</legend>
    <p>{{ age }}</p>
    <button v-on:click="incrementAge">Incrementar Idade</button>
    <button @click="decrementAge">Decrementar Idade</button>
  </fieldset>
</template>

<script>

export default {
  data(){
    return{
      age: 0,
    }
  },
  methods:{
    incrementAge(){
      return this.age++;
    },
    decrementAge(){
      return this.age--;
    }
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

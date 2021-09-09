<template>
  <div>
    <h1>VUE</h1>
  </div>
  <fieldset>
    <legend>Methods</legend>
    <p>{{ age }}</p>
    <p>Exemplo de uma expressão simples em Javascript: Contador</p>
    <button v-on:click="incrementAge">Incrementar Idade</button>
    <button @click="decrementAge">Decrementar Idade</button>
  </fieldset>

  <fieldset>
    <legend>Eventos</legend>
    <p>Utilizando a diretiva v:on ou a forma abreviada @</p>
    <fieldset><legend>Evento de mouse</legend>
    <h5>Click</h5>
      <button v-on:click="eventTest('click')">On Click</button>
      <button @click="eventTest">On click Event Param Implicit</button>
      <button @click="eventTestParam('@click', $event)">On click Event Param Explicit</button>
      <h5>Duplo click</h5>
      <button v-on:dblclick="eventTest('dbl click')">On Double Click</button>
      
    </fieldset>
    
    <fieldset><legend>Evento de mouse</legend>
      <button v-on:click.left="eventMouseTest">Mouse Left</button>
      <button v-on:click.right.prevent="eventMouseTest">Mouse Right</button>
      <button v-on:click.middle="eventMouseTest">Mouse Middle</button>
      <p @mouseenter="eventMouseTest" @mouseleave="eventMouseTest">Mouse hover test</p>
      
      </fieldset>

    <fieldset>
      <legend>Bloqueio de link com alerta</legend>
      <a :href="urlGOOGLE" v-bind:[argument]="urlGOOGLEDescription" @click.prevent="showAlert">GOOGLE</a>
    </fieldset>
    <fieldset>
      <legend>Criando um alerta apenas</legend>
      <a :href="urlGOOGLE" v-bind:[argument]="urlGOOGLEDescription" @click.prevent.once="showAlertLink">GOOGLE</a>
    </fieldset>

    <fieldset><legend>Eventos de teclado</legend>
      <input v-on:keyup.enter="eventKeyTest" placeholder="Press Enter">
      <input v-on:keydown.enter="eventKeyTest" placeholder="Press Enter e visualize a tecla apertada no console">
      <input v-on:keyup.delete="eventKeyTest" placeholder="Press Delete">
      <input v-on:keyup.space="eventKeyTest" placeholder="Press Space">
      <input v-on:keyup.esc="eventKeyTest" placeholder="Press Esc">
      <input v-on:keyup.up="eventKeyTest" placeholder="Press up">
      <input v-on:keyup.down="eventKeyTest" placeholder="Press down">
      <input v-on:keyup.left="eventKeyTest" placeholder="Press Left">
      <input v-on:keyup.right="eventKeyTest" placeholder="Press Right">
      <input v-on:keyup.tab="eventKeyTest" placeholder="Press Tab">
      <input v-on:keyup.ctrl="eventKeyTest" placeholder="Press Ctrl">
      <input v-on:keyup.alt="eventKeyTest" placeholder="Press Alt">
      <input v-on:keyup.shift="eventKeyTest" placeholder="Press Shift">
      <input v-on:keyup.meta="eventKeyTest" placeholder="Press Meta">

      <p @click.ctrl="eventTest('ctrl+click')">Ctrl + click</p>
    </fieldset>

  </fieldset>

  <fieldset><legend>Estilos</legend>
    <p v-bind:style="{ color: textColor }">inline style object</p>
    <p :style="textColorObject">inline style object bind</p>
    <p class="test-class-1" v-bind:class="testclass2">class bind</p>
    <p v-bind:class="classList">Class Bind List</p>
    <p v-bind:class="[testclass1, testclass2]">Class Bind List inline</p>
    <p :class="[1 > 0 ? testclass1 : testeclass2]">Class expression: 1 > 0 </p>
    <p :class="[4 > 3 ? 'test-class-1' : 'teste-class-2']">Class expression: 4 > 3</p>
  </fieldset>
</template>

<script>

export default {
  data(){
    return{
      click: "Clicou!",
      age: 0,
      urlGOOGLE: "https://www.google.com/",
      urlGOOGLEDescription: "Clique aqui para acessar o GOOGLE",
      textColor: "red",
      textColorObject:{
        color: 'green',
        fontSize: "25px"
      }, 
      testclass1: 'test-class-1',
      testclass2: 'test-class-2',
      classList: ["teste-class-1", "teste-class-2"]

    }
  },
  methods:{
    incrementAge(){
      return this.age++;
    },
    decrementAge(){
      return this.age--;
    },
    eventTest(name){
      console.log(name);
    },
    eventTestParam(name, event){
      console.log(name)
      console.log(event)
    },
    eventMouseTest(event){
      console.log(event.type)
    }, 
    showAlert(){
      alert("Impossível abrir o link!")
    },
    showAlertLink(){
      alert('Você será redirecionado para o GOOGLE')
    },
    eventKeyTest(event){
        console.log(event.key, event.type)
        //Enter é a tecla apertada
        //keyup é o tipo de evento
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

fieldset{
  margin-bottom: 2rem;
}

button{
  margin-left: 1.5rem;
  margin-top: 1.1rem;
}

.test-class-1{
  font-style: italic;
}
.test-class-2{
  color: blue
}

</style>

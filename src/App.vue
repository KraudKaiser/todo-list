<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :todos="todos" v-on:inputChange="childMessageReceived" />
	<h1>{{ text }}</h1>
	<input v-model="text" type="text">
	<button @click="addToNames">Enviar</button>
  </div>
</template>
<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
	return{
		text:"",
		ids:0,
		todos:[
			{
				id: 0,
				task: "Hacer la cama"
			},
			{
				id: 1,
				task: "limpiar la mesa"
			},
		]
	}
  },
  methods:{
	addToNames(){
		this.names.push(this.text)
		this.text = ""
	},
	childMessageReceived(text, index){
		console.log(text, index)
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

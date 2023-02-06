<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :todos="todos"/>
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
				id: this.ids,
				task: "Hacer la cama"
			}
		]
	}
  },
  methods:{
	addToNames(){
		this.names.push(this.text)
		this.text = ""
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

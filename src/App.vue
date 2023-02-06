<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :todos="todos" v-on:inputChange="changeTaskText" 	v-on:deleteText="deleteTask"/>
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
		if(this.todos.length == 0){
			let obj = {
				id: 0,
				task: this.text
			}
			this.todos.push(obj)
			this.text = ""
		}else{

			let lastId = this.todos[this.todos.length - 1].id + 1
			let obj = {
				id:lastId,
				task:this.text
			}
			this.todos.push(obj)
			this.text = ""
		}
		},
	changeTaskText(text, element){
		let elemento = this.todos.findIndex(result => result.id == element.id)
		this.todos[elemento].task = text
	},
	deleteTask(element){
		let elemento = this.todos.findIndex(result => result.id == element.id)
		this.todos.splice(elemento, 1)
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

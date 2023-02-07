<template>
  <div id="app">
	<img alt="Vue logo" src="./assets/logo.png">
	<h1>Bienvenido a la aplicacion de lista de Tareas sencilla con Vue JS</h1>
    <todo-list :todos="todos" v-on:sendTaskChange="changeTaskText" 	v-on:deleteText="deleteTask"/>
	<h2>Puedes ingresar una nueva tarea. Escribela abajo y haz click en enviar</h2>
	<input v-model="text" type="text">
	<button @click="addToNames">Enviar</button>
  </div>
</template>
<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
	TodoList
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
		console.log("hola")
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

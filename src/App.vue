<template>
  <div id="app">
	<img alt="Vue logo" src="./assets/logo.png">
	<h1>Bienvenido a la aplicacion de lista de Tareas sencilla con Vue JS</h1>
    <show-task :todos="todos" v-on:sendTaskChange="changeTaskText" 	v-on:deleteText="deleteTask"/>
	<h2>Puedes ingresar una nueva tarea. Escribela abajo y haz click en enviar</h2>
	<create-task v-on:sendCreateTask="createTask" />	
  </div>
</template>
<script>
import ShowTask from './components/ShowTask.vue'
import CreateTask from "./components/CreateTask.vue"
export default {
  name: 'App',
  components: {
	ShowTask,
	CreateTask
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
	createTask(text){
		if(this.todos.length == 0){
			let obj = {
				id: 0,
				task: text
			}
			this.todos.push(obj)
		}else{

			let lastId = this.todos[this.todos.length - 1].id + 1
			let obj = {
				id:lastId,
				task:text
			}
			this.todos.push(obj)
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

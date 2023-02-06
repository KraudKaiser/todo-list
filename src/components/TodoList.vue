<template>
  <div class="hello">
    <div v-bind:key="element.id" v-for="element in todos" class="todo-list" >
		<h1 >{{ element.task}}</h1>
		<input @change="changeText" type="text" placeholder="ingresa el texto nuevo" >
		<button @click="sendText(element)">Editar</button>
		<Button @click="deleteText(element)">Borrar</Button>
	</div>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  data(){
	return{
		text:""
	}
  },
  methods:{
	changeText(event){
		this.text = event.target.value
	},
	sendText(element){
		this.$emit("inputChange", this.text ,element)
		this.text = ""
	},
	deleteText(element){
		this.$emit("deleteText", element)
	}
  },
  props:{
	todos:[]
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.hello{
	display: flex;
	flex-direction: column;
	justify-content: center;
}
.todo-list{
	display: flex;
	flex-direction: row;
	justify-content: center;
	padding:1em;
	gap:0.5em;
}
</style>

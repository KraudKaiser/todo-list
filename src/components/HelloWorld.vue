<template>
  <div class="hello">
    <div v-bind:key="element.id" v-for="element in todos" class="todo-list" ref="todoDiv">
		<h1 >{{ element.task}}</h1>
		<input type="text" ref="textInput">
		<button @click="changeText">Editar</button>
		<Button >Borrar</Button>
		</div>
	
	<button>Borrar</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
	return{
		text:"hola"
	}
  },
  methods:{
	changeText(){
		let textInput = this.$refs.textInput
		this.text = textInput.value
		this.$emit("inputChange", textInput.value, this.$refs.todoDiv.index)
		textInput.value= ""
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
}
</style>

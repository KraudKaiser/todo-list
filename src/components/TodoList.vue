<template>
  <div class="hello">
    <div v-bind:key="element.id" v-for="element in todos" class="todo-list" >
		<h1 >{{ element.task}}</h1>
		<edit-text :element="element" v-on:inputChange="sendTaskChange"/>
		<delete-text :element="element" v-on:sendDeleteTask="deleteText" />
	</div>
  </div>
</template>

<script>
import EditText from "./EditText.vue"
import DeleteText from "./DeleteText.vue"
export default {
  name: 'TodoList',
  components:{
	EditText,
	DeleteText
  },
  methods:{
	deleteText(element){
		this.$emit("deleteText", element)
	},
	sendTaskChange(text, element){
		this.$emit("sendTaskChange", text, element)
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
	align-items: center;
	padding:1em;
	gap:0.5em;
}
</style>

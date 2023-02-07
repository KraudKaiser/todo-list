<template>
	<div>
		<div v-bind:key="element.id" v-for="element in todos" class="todo-list" >
			<h1>{{ element.task }}</h1>
			<edit-text :element="element" v-on:inputChange="sendTaskChange"/>
			<delete-text :element="element" v-on:sendDeleteTask="deleteText" />
		</div>
	</div>
</template>

<script>
import DeleteText from './DeleteText.vue';
import EditText from './EditText.vue';
export default {
	components:{
		DeleteText,
		EditText
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

<style>
.todo-list{
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
	padding:1em;
	gap:0.5em;
}
</style>
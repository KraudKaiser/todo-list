<template>
  <div>
	<input v-model="text" type="text" placeholder="Ingresa el texto aqui">
	<button @click="sendCreateTask">Enviar</button>
  </div>
</template>

<script>
export default {
	data(){
		return{
			text:""
		}
	},
 methods:{
	sendCreateTask(){
		this.$emit("sendCreateTask", this.text)
		this.text = ""
	}
 }
}
</script>

<style>
input{
	border: none;
	background-color: #648cfa;
	margin: 1em;
	padding: 1em;
	border-radius: 1em;
	color: #fefefe;
}
input::placeholder{
	color: #fefefe;
}

button{
	border: none;
	background-color: #32cc6d;
	color: #fefefe;
	padding: 1em;
	border-radius: 1em;
}
</style>
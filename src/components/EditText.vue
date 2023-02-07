<template>
	<div>
		<input @change="changeText" ref="input" type="text" placeholder="ingresa el texto nuevo" >
		<button @click="sendText(element)">Editar</button>
	</div>
</template>

<script>
	export default{
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
		this.$refs.input.value = ""
		}
	},
		props:{
			element:{
				
			}
		}
	}
</script>

<style scoped>
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
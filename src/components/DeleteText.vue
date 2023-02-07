<template>
	<Button @click="sendDeleteTask(element)">Borrar</Button>
</template>

<script>
export default {
	methods:{
		sendDeleteTask(element){
			this.$emit("sendDeleteTask", element)
		}
	},
	props:{
		element:{}
	}
}
</script>

<style scoped>
	button{
		border: none;
		padding: 1em;
		background-color: rgb(247, 19, 50);
		border-radius: 1em;
		color: #fefefe;
	}
</style>
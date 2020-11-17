<template>
	<form @submit.prevent="onSubmit">
		<input type="text" v-model='title' placeholder="Create your own todo" class="todo_input">
		<button class="button" type="submit"></button>
	</form>
</template>

<script>

export default {
	data() {
		return {
			title: ''
		}
	},
	methods: {
		onSubmit() {
			console.log('Submit', this.title)
			if (this.title.trim()) {
				const newToDo = {
					id: Date.now(),
					title: this.title,
					isComplete: false
				}

				this.$emit('add-todo', newToDo)
				this.title = ''
			}
		}
	}
}

</script>

<style>
	
.button {
	display:none;
}

</style>

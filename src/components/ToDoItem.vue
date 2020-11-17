<template>
	<li>
		<span class="todo_title">
			<strong class="index">{{ index + 1 }}</strong>
			{{ todo.title }}
		</span>
		<button class="rm"
				@click="$emit('remove-todo', todo.id)"
		>&#9747;</button>
	</li>
</template>

<script>

export default {
	props: {
		todo: {
					type: Object,
					required: true
				},
		index: Number
	}
}

</script>

<style scoped>

li {
	margin:0vh 2vw 1.5vh 2vw;
	display: flex;
	justify-content: space-between;
	border-bottom: 1px solid #4e6e41;
	padding-left: 1vw;
	color: #808080;
}

.rm {
	background: #4e6e41;
	color: #fff;
	border-radius: 50%;
	font-weight: bold;
	outline:none;
}

.index {
	display: none;
}

</style>
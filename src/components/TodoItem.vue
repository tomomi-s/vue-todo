<template>
	<div class="todo-item" v-bind:class="{'is-complete':todo.completed}" >
		
		<p>
			<input type="checkbox" v-on:change="markComplete">
			{{todo.title}}
			<button class="delete" @click="$emit('del-todo', todo.id)">
				x
			</button>
		</p>
	</div>
</template>

<script>
	export default{
		name: "TodoItem",
		props:["todo"],
		methods: {
			markComplete(){
				this.todo.completed = !this.todo.completed;
			}
		}
	}
</script>

<style scoped>
	.todo-item{
		padding: 10px;
		border-bottom: 1px #ccc dotted;
	}

	.is-complete{
		text-decoration: line-through;
	}

	.delete{
		width: 20px;
		height: 20px;
		color: #ffffff;
		background-color: #ff0000;
		border: none;
		border-radius: 25px;
		float: right;
	}
	
</style>
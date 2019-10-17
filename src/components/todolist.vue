<template>
	<div>
		<HelloWorld
			v-model="newTodoText"
			placeholder="New todo"
			@keydown.enter="addTodo"
		/>
		<ul v-if="todos.length">
		<news
			v-for="todo in todos"
			:key="todo.id"
			:todo="todo"
			@remove="removeTodo"
		/>
		</ul>
		<p v-else>
			你可真厉害呢，都做完了！
		</p>
	</div>
</template>

<script>
import news from './news.vue'
import HelloWorld from './HelloWorld.vue'
let nextTodoId = 1
export default {
	components: {
	news,HelloWorld
	},
	data () {
	return {
		newTodoText: '',
	todos: [
				{
				id: nextTodoId++,
				text: '学习Vue cil'
			},
				{
					id: nextTodoId++,
					text: '学习JavaScript'
				},
				{
					id: nextTodoId++,
					text: '玩耍'
				}
				]
	}
	},
methods: {
	addTodo () {
		const trimmedText = this.newTodoText.trim()
		if (trimmedText) {
			this.todos.push({
				id: nextTodoId++,
				text: trimmedText
				})
			this.newTodoText = ''
				}
			},
			removeTodo (idToRemove) {
				this.todos = this.todos.filter(todo => {
					return todo.id !== idToRemove
				})
			}
		}
	}
</script>

<style>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
	height: 60px ;
	line-height: 60px;
	font-size: 1.875rem;
	color: black;
	text-align: center;
}
a {
  color: darkred;
}
</style>

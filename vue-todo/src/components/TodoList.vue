<template>
	<ul>
		<li v-for="todo in todos.todoItems" :key="todo.id">
			<TodoItem :todo="todo" />
			<button :click="deleteTodo">제거</button>
		</li>
	</ul>
</template>

<script>
import TodoItem from "./TodoItem.vue";
import { watchEffect, reactive } from "vue";
import axios from "axios";

export default {
	components: { TodoItem },
	setup() {
		let todos = reactive({
			todoItems: [],
		});

		const getData = async () => {
			const { data } = await axios.get(`http://localhost:3001/todos`);
			// console.log(data);
			todos.todoItems = data;
		};

		// watchEffect(getData);

		watchEffect(async () => {
			const { data } = await axios.get(`http://localhost:3001/todos`);
			// console.log(data);
			todos.todoItems = data;
		});

		const deleteTodo = () => {};

		return { todos, deleteTodo };
	},
};
</script>

<style lang="scss" scoped></style>

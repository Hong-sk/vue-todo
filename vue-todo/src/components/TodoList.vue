<template>
	<ul>
		<li v-for="todo in todos.todoItems" :key="todo.id">
			<TodoItem :todo="todo" />
			{{ todo }}
		</li>
	</ul>
</template>

<script>
import TodoItem from "./TodoItem.vue";
import { watchEffect, reactive, watch } from "vue";
import axios from "axios";

export default {
	components: { TodoItem },
	setup() {
		let todos = reactive({
			todoItems: [],
		});
		watchEffect(async () => {
			const { data } = await axios.get(`http://localhost:3001/todos`);
			// console.log(data);
			todos.todoItems = data;
		});

		// const getTodos = async () => {
		// 	const { data } = await axios.get(`http://localhost:3001/todos`);
		// 	// console.log(data);
		// 	todos = data;
		// };

		return { todos };
	},
};
</script>

<style lang="scss" scoped></style>

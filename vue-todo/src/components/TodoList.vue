<template>
	<ul>
		<li v-for="todo in todos" :key="todo.id">
			<!-- <TodoItem :todo="todo" /> -->
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
		let todos = reactive([]);
		watchEffect(async () => {
			const { data } = await axios.get(`http://localhost:3001/todos`);
			// console.log(data);
			todos = data;
			console.log(todos);
		});

		const getTodos = async () => {
			const { data } = await axios.get(`http://localhost:3001/todos`);
			// console.log(data);
			todos = data;
			// console.log(todos);
		};

		getTodos();

		// watch(
		// todos,
		// async () => {
		// 	const { data } = await axios.get(`http://localhost:3001/todos`);
		// 	todos.todos = [...data];
		// 	console.log(todos);
		// },
		// {
		// 	immediate: true,
		// },
		// );

		return { todos };
	},
};
</script>

<style lang="scss" scoped></style>

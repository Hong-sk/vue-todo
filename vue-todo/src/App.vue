<template>
	<div class="container" style="margin-top: 5rem">
		<h1 style="text-align: center">Todolist</h1>
		<TodoInput />
		<TodoList />
	</div>
</template>

<script>
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
	components: { TodoInput, TodoList },
	setup() {
		return {};
	},
};
</script>

<style lang="scss" scoped></style>

<template>
	<li>
		<div>{{ todo.todoContents }}</div>
		<div>{{ todo.author }}</div>
	</li>
</template>

<script>
export default {
	props: {
		todo: Object,
	},
	setup(props) {
		// console.log(props.todo);
		console.log("it works!");
		return {};
	},
};
</script>

<style lang="scss" scoped></style>

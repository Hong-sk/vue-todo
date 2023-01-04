<template>
	<form class="row m-4" @submit.prevent="addTodo($event)">
		<div class="col-md-8">
			<input
				type="text"
				class="form-control"
				placeholder="todo를 입력하세요."
				aria-label="todo-contents"
			/>
		</div>
		<div class="col-md-2">
			<input
				type="text"
				class="form-control"
				placeholder="작성자(선택사항)"
				aria-label="author"
			/>
		</div>
		<div class="col-md-2">
			<button class="btn btn-primary">등록</button>
		</div>
		<div v-if="todoEmpty" class="checkEmpty">todo를 입력해주세요.</div>
	</form>
</template>

<script>
import axios from "axios";
import { ref } from "vue";

export default {
	setup() {
		const todoEmpty = ref(false);
		const addTodo = e => {
			if (e.target[0].value === "") {
				todoEmpty.value = true;
				return;
			} else {
				todoEmpty.value = false;
				axios.post("http://localhost:3001/todos", {
					todoContents: e.target[0].value,
					author: checkAuthor(e.target[1].value),
				});
			}
		};
		const checkAuthor = author => {
			if (author === "") {
				return "홍성권";
			} else {
				return author;
			}
		};

		return { todoEmpty, addTodo };
	},
};
</script>

<style scoped>
.checkEmpty {
	color: #c0392b;
}
</style>

<template>
	<div class="todo_cards-wrapper">
		<ToolbarPanel @addCard="addCard" />
		<TodoCard
			v-for="el in list"
			:key="el.id"
			:el="el"
			@deleteCard="deleteCard"
		/>
	</div>
</template>

<script>
import TodoCard from "./components/TodoCard.vue";
import ToolbarPanel from "./components/ToolbarPanel.vue";

export default {
	name: "App",
	components: {
		TodoCard,
		ToolbarPanel,
	},
	data() {
		return {
			list: [
				{ name: "Купить молоко", id: 1 },
				{ name: "Полить цветы", id: 2 },
				{ name: "Заказать пиццу", id: 3 },
				{ name: "Погладить собаню", id: 4 },
			],
			id: 4,
		};
	},
	methods: {
		deleteCard(event) {
			this.list = this.list.filter((el) => el.id != event);
			console.log(event);
		},
		addCard(event) {
			const newTodo = { name: event, id: ++this.id };

			this.list.unshift(newTodo);
		},
	},
};
</script>

<style lang="scss">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
	display: flex;
	justify-content: center;
}

.todo_cards-wrapper {
	flex-direction: column;
	display: flex;
	gap: 10px;
}
</style>

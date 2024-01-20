<template>
	<div class="toolbar">
		<input
			v-model="todo"
			class="toolbar-input"
			type="text"
			placeholder="Введите to do"
		/>
		<button class="toolbar-button" @click="addCard">Добавить</button>
	</div>
</template>

<script>
export default {
	name: "ToolbarPanel",
	data() {
		return {
			todo: "",
		};
	},
	methods: {
		addCard() {
			this.$emit("addCard", this.todo);
		},
	},
};
</script>

<style lang="scss" scoped>
.toolbar {
	display: flex;
	flex-direction: row;
	gap: 10px;
}

.toolbar-input {
	width: 100%;
	height: 36px;
	border-radius: 10px;
	font-size: 16px;
	font-weight: normal;
	padding: 0 15px;
	border: 1px solid #c9c9c9;
}

.toolbar-button {
	padding: 0 24px;
	font-size: 14px;
	font-weight: 600;
	border-radius: 10px;
	background: #e4f2bb;
	border: none;
	cursor: pointer;
}

.toolbar-button:hover {
	background: #dbe9b3;
}
</style>

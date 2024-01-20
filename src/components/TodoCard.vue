<template>
	<div class="todo-card" :class="{ gray: cardDisabled }" @click="toggleCard">
		<span class="todo-card__item" :class="{ 'line-through': cardDisabled }">{{
			el.name
		}}</span>
		<CloseIcon v-if="cardDisabled" @click.stop="deleteCard" />
	</div>
</template>

<script>
import CloseIcon from "./CloseIcon.vue";

export default {
	name: "TodoCard",
	props: {
		el: Object,
	},
	components: { CloseIcon },
	data() {
		return {
			cardDisabled: false,
		};
	},
	methods: {
		toggleCard() {
			this.cardDisabled = !this.cardDisabled;
		},
		deleteCard() {
			this.$emit("deleteCard", this.el.id);
		},
	},
};
</script>

<style scoped lang="scss">
.todo-card {
	width: 500px;
	height: 54px;
	padding: 0 28px;
	background-color: #e4f2bb;
	border-radius: 10px;
	display: flex;
	flex-direction: row;
	gap: 10px;
	justify-content: space-between;

	.todo-card__item {
		font-size: 16px;
		display: flex;
		align-items: center;
		text-align: center;

		&.line-through {
			text-decoration: line-through;
		}
	}
	&.gray {
		background-color: #c9c9c9;
	}

	.icon {
		cursor: pointer;
	}
}
</style>

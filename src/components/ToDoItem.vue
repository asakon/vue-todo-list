<template>
	<li class="todo-item"
		v-bind:class="{'done': done}"
		v-on:click="handleClick">
		<span v-if="done">✓</span>
		<b><slot /></b>
	</li>
</template>
<script>
export default {
	props: {
		done: {	type: Boolean }
	},
	emits: ['toggle'],
	methods: {
		handleClick() {
			this.$emit('toggle');
		}
	}
}
</script>

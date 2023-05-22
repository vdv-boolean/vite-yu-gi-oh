<script>
import { store } from '../store';

export default {
	data() {
		return {
			store,
		};
	},
};
</script>

<template>
	<div class="results-message">
		Found {{ store.characterList.length }} characters
	</div>
</template>

<style lang="scss" scoped>
.results-message {
	padding: 1rem;
	color: white;
	background-color: #1E2124;
}
</style>

<script>
import { store } from '../store';

export default {
	data() {
		return {
			store,
		};
	},
	methods: {
		emitSearchEvent() {
			this.$emit('performSearch');
            console.log("performSearch");
		},
	},
};
</script>

<template>
    <select @change="emitSearchEvent">
        <option value="">Select Archetype</option>
        <option v-for="archetype in store.archetypeList"> {{ archetype.archetype_name }}</option>
    </select>
</template>

<style scoped>

</style>
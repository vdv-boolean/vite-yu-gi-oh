<script>
import { store } from '../store';

export default {
	data() {
		return {
			store,
		};
	},
	methods: {
		search(event) {
      this.$emit("loadCards");
    },
	},
};
</script>

<template>
   <select v-model="store.archetype" @change="search">
        <option value="">Select Archetype</option>
        <option v-for="archetype in store.archetypeList" :value="archetype.archetype_name"> {{ archetype.archetype_name }}</option>
    </select>
</template>

<style scoped>

</style>
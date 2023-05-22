<script>
export default {
	props: {
		characterData: Object,
	},
};
</script>

<template>
	<div class="card">
		<img :src="characterData.card_images[0].image_url">
		<div class="info-box">
			<h1>{{ characterData.name }}</h1>
			<span>{{ characterData.archetype }}</span>
		</div>

	</div>
</template>

<style scoped>
.card {
	padding: 1rem;
	text-align: center;
}

img {
	width:100%
	}

.info-box {
	height: 100px;
	background-color: #CD843B;
	display: flex;
	flex-direction: column;
	justify-content: space-around;
}

h1 {
	color: white;
	font-size: 1rem;
	text-transform: uppercase
}
</style>

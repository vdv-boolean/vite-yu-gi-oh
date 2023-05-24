<script>
import CharacterList from './components/CharacterList.vue';
import ResultsMessage from './components/ResultsMessage.vue';
import AppSearch from './components/AppSearch.vue';
import axios from 'axios';
import { store } from './store';

export default {
	data() {
		return {
			store,
			arch: "&archetype=",
		};
	},
	components: {
		CharacterList,
		ResultsMessage,
		AppSearch,
	},
	created() {
    this.changeCards();
    this.createArchtypes();
  },
  methods: {
    changeCards(link) {
      let archLink = this.arch + link;
      if (link != null && link != "") {
        archLink = this.arch + link;
      } else {
        archLink = "";
      }
      axios
        .get(
          "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0" +
            archLink
        )
        .then((response) => (this.store.characterList = response.data.data));
    },
    createArchtypes() {
      axios
        .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then((response) => (this.store.archetypeList = response.data));
    },
  },


};
</script>

<template>
	<header>
		<nav>
			<img src="./assets/logo.jpg" alt="">
			<h1>Yu Gi Oh!</h1>
		</nav>
	</header>

	<main>
		<div class="container">
			<!-- <AppSearch @loadCards="changeCards(store.archetype)" /> -->
			<AppSearch @loadCards="changeCards(store.archetype)" />
		</div>

		<div class="container">
			<ResultsMessage />
			<CharacterList />
		</div>
	</main>
</template>

<style lang="scss">
*,
*::after,
*::before {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

body {
	background-color: #CD843B;
}

header {
	margin-bottom: 3rem;
	background-color: white;
}

nav {
	width: 1100px;
	height: 70px;
	margin: auto;
	display: flex;
	align-items: center;
	
	img {
	height: 30%;
}
}

.container {
	margin: 0 auto;
	padding: 1rem;
	max-width: 1000px;
	background-color: white;
	margin-bottom: 2rem;
}

</style>

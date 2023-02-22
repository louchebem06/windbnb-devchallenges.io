<script lang="ts">
	import type { City } from "$lib/City";
	import SearchBar from "./SearchBar.svelte";

	export let clicked: boolean;
	export let citys: City[];
	export let people: number;
	export let kidPeople: number;
	export let adultPeople: number;
	export let city: City;
	export let fnSearch: any;
</script>

<header>
	<img src="/logo.svg" alt="" class:minus={clicked}/>
	<SearchBar
		bind:clicked={clicked}
		bind:citys={citys}
		bind:people={people}
		bind:kidPeople={kidPeople}
		bind:adultPeople={adultPeople}	
		bind:city={city}
		fnSearch={fnSearch}
	/>
</header>

<style>
	header {
		max-width: 1400px;
		margin: auto auto;
		padding-top: 61px;
		padding-left: 20px;
		padding-right: 20px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	header img {
		display: block;
		height: 21px;
		width: auto;
	}

	@keyframes normalToBig {
		from {
			width: auto;
			opacity: 1;
		}
		to {
			opacity: 0;
		}
	}

	.minus {
		animation: normal 1s normalToBig;
		width: 0;
	}

	@media screen and (max-width: 500px) {
		header {
			flex-direction: column;
		}

		header img {
			position: absolute;
			top: 19px;
			left: 13px;
		}
	}
</style>

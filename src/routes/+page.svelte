<script lang="ts">
	import stays from "$lib/data/stays.json";
  	import Signature from "$lib/Signature.svelte";
  	import Stays from "$lib/Stays.svelte";
	import type { Stay as StrayInterface} from "$lib/Stay";
	import Header from "$lib/Header.svelte";
	import type { City } from "$lib/City";

	let clicked: boolean = false;
	let people: number = 0;
	let kidPeople: number = 0;
	let adultPeople: number = 0;
	let city: City;
	let citys: City[] = [];

	let staysSearch: StrayInterface[] = [];
	citys.push({city: "All", country: "finland"});
	stays.forEach((stay: any) => {
		staysSearch.push(stay);
		const tmp: City = {city: stay.city, country: stay.country};
		let isset: boolean = false;
		citys.forEach((city) => {
			if (tmp.city == city.city)
				isset = true;
		})
		if (!isset)
			citys.push(tmp);
	});
	citys = citys.slice();
	city = citys[0];

	function search() {
		staysSearch = []
		stays.forEach((stay: any) => {
			if ((stay.city == city.city || city.city == 'All')
			&& (people <= 1 || people > 1 && stay?.beds >= people ))
				staysSearch.push(stay);
		})
	}
</script>

<svelte:head>
	<title>WindBnb</title>
</svelte:head>

<Header
	bind:clicked={clicked}
	bind:citys={citys}
	bind:people={people}
	bind:kidPeople={kidPeople}
	bind:adultPeople={adultPeople}
	bind:city={city}
	fnSearch={search}
/>

{#if clicked}
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div class="opacity" on:click={() => clicked = false}></div>
{/if}

<div class="content">
	<Stays bind:stays={staysSearch} />
</div>

<Signature />

<style>
	.content {
		margin: 32px auto;
		margin-top: 61px;
		padding-bottom: 50px;
		max-width: 1400px;
	}

	@keyframes clearToBlack {
		from {
			opacity: 0;
		}
		to {
			opacity: 0.8;
		}
	}

	.opacity{
		content: " ";
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: black;
		opacity: 0.8;
		animation: normal 0.5s clearToBlack;
	}

	@media screen and (max-width: 1440px) {
		.content {
			margin: 32px 96px;
		}
	}

	@media screen and (max-width: 979px) {
		.content {
			margin: 19px 13px;
		}
	}
</style>

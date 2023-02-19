<script lang="ts">
	import stays from "$lib/data/stays.json";
  	import Signature from "$lib/Signature.svelte";
  	import Stays from "$lib/Stays.svelte";
	import type { Stay as StrayInterface} from "$lib/Stay";

	interface City {
		city: string,
		country: string
	};

	let people: any;
	let select: any;
	let city: string = "Finland";
	let citys: City[] = [];

	let staysSearch: StrayInterface[] = [];
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

	function search() {
		city = select.value;
		const beds = people?.value || 0;
		staysSearch = [];
		stays.forEach((stay: any) => {
			if ((beds <= 1 || stay.beds >= beds) && (city == "Finland" || stay.city == city))
				staysSearch.push(stay);
		});
	}
</script>

<svelte:head>
	<title>WindBnb</title>
</svelte:head>

<input bind:this={people} value={0} min=0 type="number" />
<select bind:this={select} >
	<option value="Finland">Finland</option>
	{#each citys as c}
		<option value={c.city}>{c.city}, {c.country}</option>
	{/each}
</select>

<button on:click={search}>search</button>

<div class="content">
	<Stays bind:stays={staysSearch}/>
</div>
<Signature />


<style>
	.content {
		margin: 32px 90px;
		padding-bottom: 50px;
	}

	@media screen and (max-width: 979px) {
		.content {
			margin: 19px 13px;
		}
	}
</style>

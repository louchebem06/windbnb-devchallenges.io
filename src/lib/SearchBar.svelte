<script lang="ts">
	import type { City } from "$lib/City";
	import SearchButton from "./SearchButton.svelte";
	import Select from "./Select.svelte";

	export let clicked: boolean;
	export let citys: City[];
	
	let selectedLocation: boolean = false;
	let selectedGuests: boolean = false;

	function setLocation() {
		selectedLocation = true;
		selectedGuests = false;
	}

	function setGuests() {
		selectedGuests = true;
		selectedLocation = false;
	}

	function unSelected() {
		selectedGuests = false;
		selectedLocation = false;
	}
</script>

{#if clicked}
	<!-- svelte-ignore a11y-click-events-have-key-events -->
	<div on:click={unSelected} class="backgroundSearchBar">
		<div class="headerBackgroundSearch">
			<p>Edit your search</p>
			<!-- svelte-ignore a11y-click-events-have-key-events -->
			<span class="material-symbols-rounded" on:click={() => clicked = false}>
				close
			</span>
		</div>
	</div>
{/if}
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div on:click={() => {clicked=true}} class="searchBar" class:big={clicked}>
	<Select
		bind:big={clicked}
		title="Location"
		location={true}
		bind:selected={selectedLocation}
		selectedFn={setLocation}
		elements={citys}
	/>
	<Select
		bind:big={clicked}
		title="Guests"
		location={false}
		bind:selected={selectedGuests}
		selectedFn={setGuests}
	/>
	<SearchButton bind:big={clicked} />
</div>

<style>
	.searchBar {
		background: #FFFFFF;
		box-shadow: 0px 1px 6px rgba(0, 0, 0, 0.1);
		border-radius: 16px;
		width: 297px;
		height: 55px;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: space-around;
	}

	@keyframes normalToBig {
		from {
			width: 297px;
		}
		to {
			width: 100%;
		}
	}

	.big {
		width: 100%;
		animation: normal 0.5s normalToBig;
		z-index: 2;
		cursor: default;
		justify-content: flex-start;
		position: relative;
	}

	@keyframes backgroundSearchBarFadeIn {
		0% {
			width: 0;
			height: 0;
			opacity: 0;
		}
		10% {
			width: 0;
			height: 0;
			opacity: 0;
		}
		11% {
			left: 50%;
			top: 82px;
			width: 0;
			height: 1px;
			opacity: 0.01;
		}
		20% {
			width: 100%;
			left: 0;
			top: 82px;
			height: 10px;
		}
		30% {
			width: 100%;
			height: 10px;
			top: 82px;
		} 
		75% {
			height: 162px;
			top: 0;
		}
		100% {
			width: 100%;
			top: 0;
			left: 0;
			height: 20%;
			opacity: 1;
		}
	}

	.backgroundSearchBar {
		width: 100%;
		height: 20%;
		background-color: white;
		z-index: 1;
		position: absolute;
		top: 0;
		left: 0;
		opacity: 1;
		animation: normal 1s backgroundSearchBarFadeIn;
	}

	.headerBackgroundSearch {
		opacity: 0;
		position: absolute;
		top: 18px;
		left: 22px;
		display: flex;
		width: calc(100% - 44px);
		justify-content: space-between;
		align-items: center;
		color: #333333;
		font-weight: 700;
		font-size: 12px;
		line-height: 15px;
	}

	@media screen and (max-width: 768px) {
		.headerBackgroundSearch {
			opacity: 1;
		}

		.backgroundSearchBar {
			height: 90vh;
			animation: none;
		}
	}

	@media screen and (max-width: 500px) {
		.searchBar {
			margin: 20px auto;
			width: 90%;
		}

		.backgroundSearchBar {
			width: 100%;
			height: 90vh;
			background-color: white;
			z-index: 1;
			position: absolute;
			top: 0;
			left: 0;
			opacity: 1;
			animation: none;
		}
	}
</style>

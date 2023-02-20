<script lang="ts">
	export let clicked: boolean;
</script>

{#if clicked}
	<div class="backgroundSearchBar"></div>
{/if}
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div on:click={() => {clicked=true}} class="searchBar" class:big={clicked}>

</div>

<style>
	.searchBar {
		background: #FFFFFF;
		box-shadow: 0px 1px 6px rgba(0, 0, 0, 0.1);
		border-radius: 16px;
		width: 297px;
		height: 55px;
		cursor: pointer;
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
</style>

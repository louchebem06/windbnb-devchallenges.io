<script lang="ts">
  import SearchBar from "./SearchBar.svelte";

  export let clicked: boolean;
</script>

<header>
	<img src="/logo.svg" alt="" class:minus={clicked}/>
	<SearchBar bind:clicked={clicked}/>
</header>

<style>
	header {
		max-width: 1400px;
		margin: auto;
		padding-top: 61px;
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
</style>

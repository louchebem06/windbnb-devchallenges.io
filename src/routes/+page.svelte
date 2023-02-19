<script lang="ts">
	import stays from "$lib/data/stays.json";
  	import Stay from "$lib/Stay.svelte";
</script>

<svelte:head>
	<title>WindBnb</title>
</svelte:head>

<div>
{#each stays as stay, i}
	<Stay {stay} />
{/each}
</div>

<style>
	div {
		display: flex;
		align-items: flex-start;
		justify-content: center;
		flex-wrap: wrap;
		gap: 10px;
	}
</style>
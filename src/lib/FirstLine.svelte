<script lang="ts">
	import SuperHost from "$lib/SuperHost.svelte";
	import Title from "$lib/Title.svelte";
	import Rating from "$lib/Rating.svelte";

	export let superHost: boolean;
	export let type: string;
	export let beds: number;
	export let rating: number;
</script>

<div class="firstLine">

	<div class="left">
		{#if superHost}
			<SuperHost />
		{/if}
		<Title {type} {beds}/>
	</div>

	<Rating {rating} />

</div>

<style>
	.left {
		display: flex;
		align-items: center;
		gap: 11px;
	}

	.firstLine {
		display: flex;
		justify-content: space-between;
		min-height: 35px;
		margin: 8px 0;
	}
</style>
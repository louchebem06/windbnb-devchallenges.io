<script lang="ts">
	export let type: string;
	export let beds: number | null;
</script>

<p>
	{type}
	{#if beds}
		. {beds} 
		{#if beds == 1}
		bed
		{:else}
		beds
		{/if}
	{/if}
</p>

<style>
	p {
		font-style: normal;
		font-weight: 500;
		font-size: 14px;
		line-height: 17px;
		color: #828282;
	}

	@media screen and (max-width: 979px) {
		p {
			font-size: 12px;
		}
	}
</style>

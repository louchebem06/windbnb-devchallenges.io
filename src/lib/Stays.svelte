<script lang="ts">
	import type { Stay as StrayInterface} from "$lib/Stay";
	import Stay from "$lib/Stay.svelte";

	export let stays: StrayInterface[];
</script>

<div class="header">
	<h1>Stays in Finland</h1>
	<p>{stays.length}+ stays</p>
</div>
<div class="stays">
	{#each stays as stay}
		<Stay {stay} />
	{/each}
</div>

<style>
	.stays {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		gap: 10px;
	}

	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 32px;
	}

	.header p {
		font-style: normal;
		font-weight: 500;
		font-size: 14px;
		line-height: 17px;
		color: #4F4F4F;
	}

	.header h1 {
		font-style: normal;
		font-weight: 700;
		font-size: 24px;
		line-height: 29px;
		color: #333333;
	}

	@media screen and (max-width: 979px) {
		.stays {
			gap: 5px;
		}

		.header h1 {
			font-size: 18px;
		}

		.header {
			margin-bottom: 24px;
		}
	}

	@media screen and (max-width: 935px) {
		.stays {
			justify-content: space-around;
		}
	}
</style>

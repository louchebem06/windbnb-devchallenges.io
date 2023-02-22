<script lang="ts">
	export let big: boolean;
	export let fnSearch: any;
</script>

<button class:big={big} on:click={fnSearch}>
	<span class="material-symbols-rounded">
		search
	</span>
	{#if big}
		<p>Search</p>
	{/if}
</button>

<style>
	button {
		background-color: transparent;
		border: none;
		cursor: pointer;
	}

	button span {
		color: #EB5757;
	}

	button.big span {
		color: #F2F2F2;
	}

	.big {
		background: #EB5757;
		box-shadow: 0px 1px 6px rgba(0, 0, 0, 0.1);
		border-radius: 16px;
		color: #F2F2F2;
		width: 127px;
		height: 48px;
		display: flex;
		justify-content: center;
		align-items: center;
		gap: 11px;
		margin: auto;
	}

	@media screen and (max-width: 768px) {
		.big {
			position: absolute;
			top: 69vh;
			left: 50%;
			transform: translate(-50%);
		}
	}
</style>

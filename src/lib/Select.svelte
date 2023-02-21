<script lang="ts">
  	import type { City } from "$lib/City";
	import LocateElement from "./LocateElement.svelte";
  	import People from "./People.svelte";

	export let big: boolean;
	export let location: boolean;
	export let title: string;
	export let selected: boolean;
	export let selectedFn: any;
	export let elements: City[] = [];
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div on:click={selectedFn} class="content" class:big={big} class:selected={selected && big}>
	{#if big}
		<h3>{title}</h3>
	{/if}
	<p class:location={location} class:people={!location}>Coucou</p>

	{#if selected && elements.length && big}
		<div class="elements">
			{#each elements as element }
				<LocateElement {element} />
			{/each}
		</div>
	{/if}
	{#if selected && big && !location}
		<div class="elements">
			<People title="Adults" subTitle="Ages 13 or above" value={0}/>
			<People title="Children" subTitle="Ages 2-12" value={0}/>
		</div>
	{/if}
</div>

<style>
	.content {
		width: 33%;
		height: 55px;
		padding-left: 15px;
		cursor: pointer;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.selected {
		border: 1px solid #333333;
		filter: drop-shadow(0px 1px 6px rgba(0, 0, 0, 0.1));
		border-radius: 16px;
	}

	.big {
		padding-left: 30px;
		position: relative;
	}

	@keyframes goVisibility {
		0% {
			opacity: 0;
		}
		50% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	.elements {
		--size: 250px;
		--padding: 25px;
		position: absolute;
		bottom: calc(calc(var(--size) + 41px) * -1);
		left: 0;
		width: calc(100% - calc(var(--padding) * 2));
		height: var(--size);
		padding: 0 var(--padding);
		display: flex;
		flex-direction: column;
		gap: 35px;
		animation: 1s goVisibility;
	}

	.content p {
		position: relative;
		width: 100%;
		font-weight: 400;
		font-size: 14px;
	}

	.content p:after {
		position: absolute;
		content: " ";
		background-color: #F2F2F2;
		right: 0;
		top: -18px;
		width: 1px;
		height: 55px;
	}

	.content h3 {
		font-weight: 800;
		font-size: 9px;
		/* line-height: 11px; */
		text-transform: uppercase;
		color: #333333;
	}

	.content .location {
		color: #333333;
	}

	.content .people {
		color: #BDBDBD;
	}
</style>

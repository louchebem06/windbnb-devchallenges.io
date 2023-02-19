<script lang="ts">
	import type { Stay } from "$lib/Stay";
	import FirstLine from "$lib/FirstLine.svelte";

	export let stay: Stay;
</script>

<div class="stay">
	<img src="{stay.photo}" alt="" />
	<FirstLine
		superHost={stay.superHost}
		beds={stay.beds}
		type={stay.type}
		rating={stay.rating}
	/>
	<h2>{stay.title}</h2>
</div>

<style>
	.stay {
		max-width: 395px;
	}

	.stay img {
		width: 395px;
		height: 269px;
		border-radius: 24px;
		max-height: 269px;
		object-fit: cover;
	}

	.stay h2 {
		font-style: normal;
		font-weight: 600;
		font-size: 16px;
		line-height: 20px;
		text-align: right;
		color: #333333;
		text-align: left;
	}
</style>

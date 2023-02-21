<script lang="ts">
	import type { City } from "$lib/City";
	
	export let element: City;
</script>

<div class="locate">
	<span class="material-symbols-rounded">
		location_on
	</span>
	<h6>{element.city}, {element.country}</h6>
</div>

<style>
	.material-symbols-rounded {
		font-variation-settings:
		'FILL' 1,
		'wght' 400,
		'GRAD' 0,
		'opsz' 24
	}

	h6 {
		font-weight: 400;
		font-size: 14px;
		line-height: 18px;
	}

	.locate {
		display: flex;
		justify-content: flex-start;
		align-items: center;
		color: #4F4F4F;
		gap: 10px;
	}

	.locate:hover {
		opacity: 0.8;
	}
</style>
<script lang="ts">
	export let rating: number;
</script>

<div class="rating">
	<span class="material-symbols-rounded">
		star
	</span>		
	<p>{rating}</p>
</div>

<style>
	.material-symbols-rounded {
		font-variation-settings:
		'FILL' 1
	}

	.rating {
		display: flex;
		align-items: center;
		gap: 7.12px;
	}

	.rating span {
		color: #EB5757;
		width: 16px;
		height: 16px;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 22px;
	}

	.rating p {
		font-style: normal;
		font-weight: 500;
		font-size: 14px;
		line-height: 17px;
		color: #4F4F4F;
	}

	@media screen and (max-width: 979px) {
		.rating p {
			font-size: 12px;
		}

		.rating span {
			font-size: 20px;
		}
	}
</style>

<script lang="ts">
	export let value: number;
	export let title: string;
	export let subTitle: string;

	function minus() {
		if (value > 0)
			value--;
	}

	function plus() {
		value++;
	}
</script>

<div class="calculate">
	<h2>{title}</h2>
	<h3>{subTitle}</h3>
	<div class="calc">
		<button on:click={minus}>-</button>
		<h4>{value}</h4>
		<button on:click={plus}>+</button>
	</div>
</div>

<style>
	.calc {
		display: flex;
		align-items: center;
		gap: 15px;
		margin-top: 12px;
		user-select: none;
	}

	.calc button {
		background: transparent;
		border: 1px solid #828282;
		border-radius: 4px;
		--size: 24px;
		width: var(--size);
		height: var(--size);
		cursor: pointer;
	}

	.calculate h2, .calculate h3 {
		font-style: normal;
		font-weight: 700;
		font-size: 14px;
		line-height: 18px;
	}

	.calculate h2 {
		color: #333333;
	}

	.calculate h3 {
		color: #BDBDBD;
	}
</style>

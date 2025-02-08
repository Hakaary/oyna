<script>
	export let height = '70px';
	export let width = '140px';
	export let color;
	export let label;
</script>

<div class="label">
	<div class="square" style="background-color: {color}; height: {height}; width: {width};">
		{label}
	</div>
	<div class="pointer">
		<div class="triangle" style="background-color: {color};" />
	</div>
</div>

<style>
	.label {
		display: flex;
	}

	.square {
		height: 70px;
		width: 140px;
		border-radius: 8px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.pointer {
		display: flex;
		align-items: center;
	}

	.triangle {
		height: 30px;
		width: 16px;
		clip-path: polygon(100% 50%, 0 0, 0 100%);
	}
</style>

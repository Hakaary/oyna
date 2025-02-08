<script>
	export let Icon;

	export let height = '70px';
	export let width = '180px';
	export let color;
	export let label;

	export let spacerWidth = '16px';
	export let iconPaddingLeft = '10px';
	export let iconSize = '2.5rem';

	export let link;
</script>

<div class="label">
	<a
		class="square"
		style="background-color: {color}; height: {height}; width: {width}; padding-left: {iconPaddingLeft};"
		href={link}
		target="_blank"
	>
		<div class="square-icon">
			<svelte:component this={Icon} color="white" size={iconSize} />
		</div>
		<div class="spacer" style="width: {spacerWidth};" />
		<span id="label-text">
			{label}
		</span>
	</a>
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
		border-radius: 8px;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		transition: transform 0.3s;
		text-decoration: none;
		color: var(--text-1);
	}

	.square:hover {
		cursor: pointer;
		transform: scale(1.15);
	}

	.square-icon {
		transition: transform 0.3s;
	}

	.square:hover .square-icon {
		transform: rotate(360deg);
	}

	#label-text {
		user-select: none;
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

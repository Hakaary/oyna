<script>
	import { onMount } from 'svelte';

	export let name;
	export let url;
	export let image1;
	export let image1YDisplacement;
	export let image1YDisplacementHover;
	export let image1Scale = "100%";
	export let image2;
	export let image2YDisplacement;
	export let image2YDisplacementHover;
	export let image2WideStyle = false;
	export let boxGradColour;
	export let boxGradColourHover;

	let link;
	let image1Deg;
	let image2Deg;
	let image1Html;
	let image2Html;

	onMount(() => {
		link.addEventListener('mouseenter', () => {
			image1Deg.style.background = `linear-gradient(30deg, ${boxGradColourHover} 0.5%, transparent)`;
			image2Deg.style.background = `linear-gradient(-30deg, ${boxGradColourHover} 0.5%, transparent)`;
			image1Html.style.transform = `translateY(${image1YDisplacementHover}) scale(${image1Scale})`;
			image2Html.style.transform = `translateY(${image2YDisplacementHover})`;
		});
		link.addEventListener('mouseleave', () => {
			image1Deg.style.background = `linear-gradient(30deg, ${boxGradColour} 0.5%, transparent)`;
			image2Deg.style.background = `linear-gradient(-30deg, ${boxGradColour} 0.5%, transparent)`;
			image1Html.style.transform = `translateY(${image1YDisplacement}) scale(${image1Scale})`;
			image2Html.style.transform = `translateY(${image2YDisplacement})`;
		});

		if (image2WideStyle === true) {
			image2Html.style.width = "100%";
			image2Html.style.height = "120%";
		} else {
			image2Html.style.width = "100%";
			image2Html.style.height = "auto";
		}
	});
</script>

<a class="project-link" href={url} target="_blank" bind:this={link}>
	<div class="project-image-box">
		<img
			class="project-image-lang"
			src={image1}
			alt={name}
			style="transform: translateY({image1YDisplacement}) scale({image1Scale})"
			bind:this={image1Html}
		/>
		<div
			class="project-image-deg"
			style="
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background: linear-gradient(30deg, {boxGradColour} 0.5%, transparent);
		pointer-events: none;
		"
			bind:this={image1Deg}
		></div>
		<h3 class="project-name">{name}</h3>
	</div>
	<div class="project-image-box">
		<img
			class="project-image-prj"
			src={image2}
			alt={name}
			style="transform: translateY({image2YDisplacement})"
			bind:this={image2Html}
		/>
		<div
			class="project-image-deg"
			style="
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background: linear-gradient(-30deg, {boxGradColour} 0.5%, transparent);
		pointer-events: none;
		"
			bind:this={image2Deg}
		></div>
	</div>
</a>

<style>
	.project-link {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		overflow: hidden;
		color: inherit;
	}

	.project-name {
		position: absolute;
		margin: 0;
		padding: 0;
		top: 5%;
		left: 2%;
		text-transform: uppercase;
		font-size: 45px;
	}

	.project-image-box {
		position: relative;
		height: 100%;
		width: 100%;
		overflow: hidden;
	}

	.project-image-lang {
		position: absolute;
		width: 100%;
		height: auto;
		object-fit: cover;
		transition: transform 0.5s;
	}

	.project-image-prj {
		position: absolute;
		object-fit: cover;
		transition: transform 0.5s;
		mask-image: linear-gradient(to right, rgba(0, 0, 0, 0), rgba(0, 0, 0, 1));
	}
</style>

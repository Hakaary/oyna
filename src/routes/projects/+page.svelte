<script>
	import { onMount } from 'svelte';

	let colourIt = 0;
	let colours = [
		// "#cd412b",
		'#9ea5a8',
		// "#27343a",
	];
	const getNextColourIt = () => {
		return colours[colourIt++ % colours.length];
	};

	let projects = [
		{
			name: 'Manga Reader',
			url: 'https://github.com/Hakaary/manga-reader',
			image: '/langs/java.png',
			wrapper: null,
			link: null
		},
		{
			name: 'Rust Manga Scrapper',
			url: 'https://github.com/Hakaary/rust-manga-scrapper',
			image: '/langs/rust.png',
			wrapper: null,
			link: null
		},
		{
			name: 'Python Snake',
			url: 'https://github.com/Hakaary/python_snake',
			image: '/langs/python.png',
			wrapper: null,
			link: null
		},
		{
			name: 'Manga Reader',
			url: 'https://github.com/Hakaary/manga-reader',
			image: '/langs/java.png',
			wrapper: null,
			link: null
		},
		{
			name: 'Rust Manga Scrapper',
			url: 'https://github.com/Hakaary/rust-manga-scrapper',
			image: '/langs/rust.png',
			wrapper: null,
			link: null
		},
		{
			name: 'Python Snake',
			url: 'https://github.com/Hakaary/python_snake',
			image: '/langs/python.png',
			wrapper: null,
			link: null
		}
	];

	onMount(() => {
		projects.map((project) => {
			project.wrapper.addEventListener('mouseenter', () => {
				project.link.style.transform = 'scaleY(150%)';
				project.wrapper.style.zIndex = '1';
			});
			project.wrapper.addEventListener('mouseleave', () => {
				project.link.style.transform = 'scaleY(100%)';
				project.wrapper.style.zIndex = '0';
			});
			// project.link.style.transition = "transform 1s";
			project.wrapper.style.zIndex = '0';
		});
	});
</script>

<main id="projects">
	{#each projects as project}
		<div class="project-wrapper" bind:this={project.wrapper}>
			<a
				class="project-link"
				href={project.url}
				target="_blank"
				style="background-color: {getNextColourIt()};"
				bind:this={project.link}
			>
			</a>
			<img class="project-image" src={project.image} alt={project.name} />
		</div>
	{/each}
</main>

<style>
	#projects {
		padding: 0px;
		display: flex;
		height: 100vh;
		flex-direction: column;
		justify-content: space-around;
		overflow: hidden;
	}

	.project-wrapper {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.project-image {
		position: fixed;
		height: 270px;
	}

	.project-link {
		position: relative;
		width: 100%;
		height: 100%;
		text-decoration: none;
		color: inherit;
		background-image: linear-gradient(to top, rgba(255,0,0,0), rgba(255,0,0,0.5));
	}
</style>

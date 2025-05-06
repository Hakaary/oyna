<script>
	import LabelProject from '$lib/Labels/LabelProject.svelte';

	let colourIt = 0;
	let colours = ['rgb(205 65 43 / 50%)', 'rgb(39 52 58 / 90%)'];
	const getNextColour = () => {
		return colours[colourIt++ % colours.length];
	};

	let boxGradColourHover = 'rgb(255 255 255 / 12%)';

	let projects = [
		{
			name: 'Manga Reader',
			url: 'https://github.com/Hakaary/manga-reader',
			image1: '/langs/java.png',
			image1YDisplacement: '-35%',
			image1YDisplacementHover: '-42%',
			image2: '/langs/java.png',
			image2YDisplacement: '0%',
			image2YDisplacementHover: '0%',
			image2WideStyle: false,
			boxGradColour: getNextColour()
		},
		{
			name: 'Manga Web Scrapper',
			url: 'https://github.com/Hakaary/rust-manga-scrapper',
			image1: '/langs/rust.png',
			image1YDisplacement: '-15%',
			image1YDisplacementHover: '-30%',
			image2: '/projects/manga_web_scrapper.png',
			image2YDisplacement: '0%',
			image2YDisplacementHover: '-10%',
			image2WideStyle: true,
			boxGradColour: getNextColour()
		},
		{
			name: 'Snake on CLI',
			url: 'https://github.com/Hakaary/python_snake',
			image1: '/langs/python.png',
			image1YDisplacement: '-0.5%',
			image1YDisplacementHover: '-8%',
			image2: '/projects/python_snake.png',
			image2YDisplacement: '-44%',
			image2YDisplacementHover: '-48%',
			image2WideStyle: false,
			boxGradColour: getNextColour()
		},
		{
			name: 'Portfolio page',
			url: 'https://github.com/Hakaary/oyna',
			image1: '/langs/javascript.png',
			image1YDisplacement: '-25%',
			image1YDisplacementHover: '-35%',
			image2: '/langs/javascript.png',
			image2YDisplacement: '0%',
			image2YDisplacementHover: '0%',
			image2WideStyle: false,
			boxGradColour: getNextColour()
		}
	];
</script>

<main id="projects">
	<ul class="projects-list">
		{#each projects as project}
			<li class="projects-list-element">
				<LabelProject
					name={project.name}
					url={project.url}
					image1={project.image1}
					image1YDisplacement={project.image1YDisplacement}
					image1YDisplacementHover={project.image1YDisplacementHover}
					image2={project.image2}
					image2YDisplacement={project.image2YDisplacement}
					image2YDisplacementHover={project.image2YDisplacementHover}
					boxGradColour={project.boxGradColour}
					image2WideStyle={project.image2WideStyle}
				/>
			</li>
		{/each}
	</ul>
</main>

<style>
	#projects {
		padding: 0px;
		height: 100vh;
	}

	.projects-list {
		height: 100%;
		list-style: none;
		display: flex;
		flex-direction: column;
		overflow: hidden;
	}

	.projects-list-element {
		display: flex;
		flex: 1;
	}
</style>

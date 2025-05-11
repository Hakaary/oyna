<script>
	import LabelProject from '$lib/Labels/LabelProject.svelte';

	let colourIt = 0;
	let colours = ['rgb(205 65 43 / 50%)', 'rgb(39 52 58 / 90%)'];
	const getNextColour = () => {
		return colours[colourIt++ % colours.length];
	};

	// let boxGradColourHover = 'rgb(90 90 90 / 40%)';

	let projects = [
		{
			name: 'Manga Reader',
			url: 'https://github.com/Hakaary/manga-reader',
			image1: '/langs/java.svg',
			image1YDisplacement: '-16%',
			image1YDisplacementHover: '-30%',
			image1Scale: "120%",
			image2: '/projects/manga_reader.png',
			image2YDisplacement: '-22%',
			image2YDisplacementHover: '-24%',
			image2WideStyle: false,
			boxGradColour: getNextColour()
		},
		{
			name: 'Manga Web Scrapper',
			url: 'https://github.com/Hakaary/rust-manga-scrapper',
			image1: '/langs/rust.png',
			image1YDisplacement: '-25%',
			image1YDisplacementHover: '-35%',
			image1Scale: "70%",
			image2: '/projects/manga_web_scrapper.png',
			image2YDisplacement: '0%',
			image2YDisplacementHover: '-7%',
			image2WideStyle: true,
			boxGradColour: getNextColour()
		},
		{
			name: 'Snake on CLI',
			url: 'https://github.com/Hakaary/python-snake',
			image1: '/langs/python.png',
			image1YDisplacement: '-18%',
			image1YDisplacementHover: '-28%',
			image1Scale: "68%",
			image2: '/projects/python_snake.png',
			image2YDisplacement: '-44%',
			image2YDisplacementHover: '-46%',
			image2WideStyle: false,
			boxGradColour: getNextColour()
		},
		{
			name: 'Portfolio page',
			url: 'https://github.com/Hakaary/oyna',
			image1: '/langs/javascript.png',
			image1YDisplacement: '-25%',
			image1YDisplacementHover: '-35%',
			image1Scale: "80%",
			image2: '/langs/oyna.png',
			image2YDisplacement: '0%',
			image2YDisplacementHover: '-8%',
			image2WideStyle: true,
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
					image1Scale={project.image1Scale}
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

<script>
	import TextChanger from '$lib/TextChanger/TextChanger.svelte';
</script>

<main id="home">
	<ul class="column column-1">
		<li class="column-1-element intro">
			<span class="column-1-text intro"> Hello, it's me </span>
		</li>
		<li class="column-1-element name">
			<span class="column-1-text name"> Luis Reyero </span>
		</li>
		<li class="column-1-element role">
			<span class="column-1-text role"> developer </span>
		</li>
		<li class="column-1-element space" />
		<li class="column-1-element window">
			<span class="column-1-text window">
				and this is my <TextChanger color="var(--text-3)" />
			</span>
		</li>
		<li class="column-1-element window">
			<span class="column-1-text window"> to the world </span>
		</li>
	</ul>
	<ul class="column column-2">
		<li class="column-2-element"><span>PHOTO</span></li>
	</ul>
</main>

<style>
	#home {
		display: flex;
		flex-direction: row;
		padding-left: 6.5rem;
		padding-top: 20vh;
	}

	.column {
		width: 50%;
		text-align: left;
		list-style: none;
	}

	.column-1-element.intro {
		font-size: 40px;
	}

	.column-1-text.name {
		font-size: 80px;
	}

	.column-1-text.role {
		font-size: 50px;
		color: var(--text-3);
	}

	.column-1-element.space {
		height: 80px;
	}

	.column-1-element.window {
		font-size: 50px;
		color: var(--text-1);
	}

	.column-1-text.window {
		display: flex;
		align-items: center;
	}

	@media (min-width: 1351px) {
		.column {
			height: auto;
		}
	}

	@media (max-width: 1350px) {
		#home {
			flex-direction: column;
		}

		.column {
			width: 100%;
		}
	}
</style>

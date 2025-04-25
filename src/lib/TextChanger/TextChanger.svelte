<script>
	import { onMount, onDestroy } from 'svelte';

	export let words = ['example1', 'example2'];
	export let color = 'white';

	const space = '\u00A0';

	let currentWordDisplay;
	let currentIndex = 0;
	let currentWord = words[currentIndex];
	let interval;

	const shuffleWord = () => {
		currentIndex++;
		if (currentIndex >= words.length) {
			currentIndex = 0;
		}
		currentWord = space + words[currentIndex];
		currentWordDisplay.textContent = currentWord;
	};

	onMount(() => {
		interval = setInterval(() => {
			shuffleWord();
		}, 1000);
	});

	onDestroy(() => {
		clearInterval(interval);
	});
</script>

<div id="scroller">
	<span id="text" bind:this={currentWordDisplay} style="color: {color};">{space + words[0]}</span>
</div>

<style>
	#scroller {
		overflow: hidden;
		position: relative;
	}

	#text {
		display: inline-block;
		line-height: 1em;
	}
</style>

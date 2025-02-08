<script>
	import { onMount, onDestroy } from 'svelte';

	const words = [
		'\u00A0ventana',
		'\u00A0fenêtre',
		'\u00A0окно',
		'\u00A0窗口',
		'\u00A0finestra',
		'\u00A0raam',
		'\u00A0Fenster',
		'\u00A0oyna',
		'\u00A0vindu',
		'\u00A0窓',
		'\u00A0fereastră',
		'\u00A0window',
		'\u00A0fönster'
	];

	export let color = 'white';

	let currentWordDisplay;
	let currentIndex = 0;
	let currentWord = words[currentIndex];

	let interval;

	const shuffleWord = () => {
		currentIndex++;
		if (currentIndex >= words.length) {
			currentIndex = 0;
		}
		currentWord = words[currentIndex];
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
	<span id="text" bind:this={currentWordDisplay} style="color: {color};">{words[0]}</span>
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

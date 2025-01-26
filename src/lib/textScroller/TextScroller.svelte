<script>
	import { onMount } from 'svelte';

	const words = [
		'ventana',
		'fenêtre',
		'janela',
		'окно',
		'pencere',
		'raam',
		'okno',
		'bintana',
		'dirisha',
		'Fenster',
		'vindue',
		'ikkuna',
		'okno',
		'finestra',
		'прозор',
		'ablak',
		'oyna',
		'window'
	];

	export let color = 'white';

	let currentWordDisplay;
	let currentIndex = 0;
	let currentWord = words[currentIndex];

	const shuffleWord = () => {
		currentIndex++;
		if (currentIndex >= words.length) {
			currentIndex = 0;
		}
		currentWord = words[currentIndex];
		currentWordDisplay.textContent = currentWord;
	};

	onMount(() => {
		setInterval(() => {
			shuffleWord();
		}, 500); // Cambiar cada segundo
	});
</script>

<span id="text" bind:this={currentWordDisplay} style="color: {color};">{words[0]}</span>

<style>
</style>

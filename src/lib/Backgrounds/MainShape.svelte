<script>
	export let color = 'white';
</script>

<div id="home-shape" style="background-color: {color};">TEST</div>

<style>
	#home-shape {
		clip-path: polygon(0 0, 100% 0%, 100% 40%, 0 80%);
		width: 100%;
		height: 100%;
		position: absolute;
		opacity: 25%;
		z-index: -1;
	}
</style>

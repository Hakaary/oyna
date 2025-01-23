<script>
	export let color = 'red';
	export let size = '2rem';
	export let margin = '0 1.5rem';
</script>

<svg
	xmlns="http://www.w3.org/2000/svg"
	viewBox="0 -960 960 960"
	height={size}
	width={size}
	fill={color}
	style="margin: {margin}"
>
	<path
		d="M240-200h120v-240h240v240h120v-360L480-740 240-560v360Zm-80 80v-480l320-240 320 240v480H520v-240h-80v240H160Zm320-350Z"
	/>
</svg>

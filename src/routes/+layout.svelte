<script>
	import Navbar from '$lib/navbar/Navbar.svelte';
	import MainShape from '$lib/shapes/MainShape.svelte';
	import '../app.css';
</script>

<Navbar navbarColor="var(--bg-4)" hoverColor="var(--bg-3)" elementsColor="var(--text-1)" />
<MainShape color="var(--bg-3)" />
<slot />

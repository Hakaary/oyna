<script>
	import HomeIcon from '$lib/Navbar/icons/HomeIcon.svelte';
	import RoadMapIcon from '$lib/Navbar/icons/RoadmapIcon.svelte';
	import EducationIcon from '$lib/Navbar/icons/EducationIcon.svelte';
	import ProjectsIcon from '$lib/Navbar/icons/ProjectsIcon.svelte';
	import ContactIcon from '$lib/Navbar/icons/ContactIcon.svelte';
	import ExpandIcon from '$lib/Navbar/icons/ExpandIcon.svelte';
	import CollapseIcon from '$lib/Navbar/icons/CollapseIcon.svelte';
	import { onMount } from 'svelte';

	export let navbarColor = 'white';
	export let hoverColor = 'red';
	export let elementsColor = 'black';

	let navbar;
	let navbarCollapsed = true;
	let navbarWidth = '5rem';
	let navbarIcon = ExpandIcon;

	let coverBackground;

	const alternateNavbarState = () => {
		navbarCollapsed = !navbarCollapsed;
		navbarWidth = navbarCollapsed ? '5rem' : '14rem';
		navbarIcon = navbarCollapsed ? ExpandIcon : CollapseIcon;
		navbar.style.width = navbarWidth;
		coverBackground.style.display = navbarCollapsed ? 'none' : 'block';
		coverBackground.style.height = navbarCollapsed ? '0%' : '100%';
	};

	onMount(() => {
		navbar.addEventListener('transitionend', (event) => {
			if (event.propertyName === 'width') {
				document.querySelectorAll('.navbar-text').forEach((span) => {
					span.style.display = navbarCollapsed ? 'none' : 'block';
				});
			}
		});
		navbar.addEventListener('transitionstart', (event) => {
			if (event.propertyName === 'width' && navbarCollapsed) {
				document.querySelectorAll('.navbar-text').forEach((span) => {
					span.style.display = navbarCollapsed ? 'none' : 'block';
					document.querySelector('.cover-background').style.height = '0%';
				});
			}
		});
	});
</script>

<nav class="navbar" bind:this={navbar} style="background-color: {navbarColor};">
	<ul class="navbar-list">
		<li class="navbar-list-element" style="--hover-color: {hoverColor};">
			<a class="navbar-element-link" href="/home" style="color: {elementsColor};">
				<HomeIcon color={elementsColor} />
				<span class="navbar-text">HOME</span>
			</a>
		</li>
		<li class="navbar-list-element" style="--hover-color: {hoverColor};">
			<a class="navbar-element-link" href="/roadmap" style="color: {elementsColor};">
				<RoadMapIcon color={elementsColor} />
				<span class="navbar-text">ROADMAP</span>
			</a>
		</li>
		<li class="navbar-list-element" style="--hover-color: {hoverColor};">
			<a class="navbar-element-link" href="/education" style="color: {elementsColor};">
				<EducationIcon color={elementsColor} />
				<span class="navbar-text">EDUCATION</span>
			</a>
		</li>
		<li class="navbar-list-element" style="--hover-color: {hoverColor};">
			<a class="navbar-element-link" href="/projects" style="color: {elementsColor};">
				<ProjectsIcon color={elementsColor} />
				<span class="navbar-text">PROJECTS</span>
			</a>
		</li>
		<li class="navbar-list-element" style="--hover-color: {hoverColor};">
			<a class="navbar-element-link" href="/contact" style="color: {elementsColor};">
				<ContactIcon color={elementsColor} />
				<span class="navbar-text">CONTACT</span>
			</a>
		</li>
		<li class="navbar-list-element" style="--hover-color: {hoverColor};">
			<button class="cover" on:click={alternateNavbarState} aria-label="Toggle Navbar">
				<svelte:component this={navbarIcon} color={elementsColor} />
			</button>
		</li>
	</ul>
</nav>
<button
	bind:this={coverBackground}
	class="cover-background"
	on:click={alternateNavbarState}
	aria-label="Toggle Navbar"
/>

<style>
	.navbar {
		width: 5rem;
		height: 100vh;
		position: fixed;
		transition: width 0.15s;
		z-index: 9999;
	}

	.navbar-list {
		list-style: none;
		padding: 0;
		margin: 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 100%;
	}

	.navbar-list-element {
		width: 100%;
		transition: background-color 0.2s;
	}

	.navbar-list-element:hover {
		background-color: var(--hover-color);
	}

	.navbar-list-element:last-child {
		margin-top: auto;
	}

	.navbar-element-link {
		display: flex;
		align-items: center;
		height: 5rem;
		text-decoration: none;
	}

	.navbar-text {
		display: none;
		font-size: 1.3rem;
		animation: fadeIn 0.2s;
	}

	.cover-background {
		display: none;
		width: 100%;
		height: 0%;
		position: fixed;
		background-color: rgba(0, 0, 0, 0.6);
		margin-left: 5rem;
		animation: fadeIn 0.2s;
		cursor: default;
		z-index: 9998;
	}

	.cover {
		all: unset;
		display: inline-block;
		cursor: pointer;
		height: 5rem;
		width: 100%;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}
</style>

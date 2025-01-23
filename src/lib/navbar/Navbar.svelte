<script>
	import HomeIcon from '$lib/navbar/icons/HomeIcon.svelte';
	import RoadMapIcon from '$lib/navbar/icons/RoadmapIcon.svelte';
	import EducationIcon from '$lib/navbar/icons/EducationIcon.svelte';
	import ProjectsIcon from '$lib/navbar/icons/ProjectsIcon.svelte';
	import ContactIcon from '$lib/navbar/icons/ContactIcon.svelte';
	import ExpandIcon from '$lib/navbar/icons/ExpandIcon.svelte';
	import CollapseIcon from '$lib/navbar/icons/CollapseIcon.svelte';
	import { onMount } from 'svelte';

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

	const collapseNavbar = () => {
		if (!navbarCollapsed) {
			alternateNavbarState();
		}
	};

	onMount(() => {
		navbar.addEventListener('transitionend', (event) => {
			if (event.propertyName === 'width') {
				document.querySelectorAll('span').forEach((span) => {
					span.style.display = navbarCollapsed ? 'none' : 'block';
				});
			}
		});
		navbar.addEventListener('transitionstart', (event) => {
			if (event.propertyName === 'width' && navbarCollapsed) {
				document.querySelectorAll('span').forEach((span) => {
					span.style.display = navbarCollapsed ? 'none' : 'block';
					document.querySelector('.cover-background').style.height = '0%';
				});
			}
		});
	});
</script>

<nav bind:this={navbar}>
	<ul>
		<li>
			<a href="/home">
				<HomeIcon color="var(--text-1)" />
				<span>HOME</span>
			</a>
		</li>
		<li>
			<a href="/roadmap">
				<RoadMapIcon color="var(--text-1)" />
				<span>ROADMAP</span>
			</a>
		</li>
		<li>
			<a href="/education">
				<EducationIcon color="var(--text-1)" />
				<span>EDUCATION</span>
			</a>
		</li>
		<li>
			<a href="/projects">
				<ProjectsIcon color="var(--text-1)" />
				<span>PROJECTS</span>
			</a>
		</li>
		<li>
			<a href="/contact">
				<ContactIcon color="var(--text-1)" />
				<span>CONTACT</span>
			</a>
		</li>
		<li>
			<button on:click={alternateNavbarState} aria-label="Toggle Navbar">
				<svelte:component this={navbarIcon} color="var(--text-1)" />
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
	nav {
		width: 5rem;
		height: 100vh;
		position: fixed;
		background-color: var(--bg-4);
		transition: width 0.15s;
		z-index: 9999;
	}

	ul {
		list-style: none;
		padding: 0;
		margin: 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		height: 100%;
	}

	li {
		width: 100%;
		transition: background-color 0.2s;
	}

	li:hover {
		background-color: var(--bg-3);
	}

	li:last-child {
		margin-top: auto;
	}

	a {
		display: flex;
		align-items: center;
		height: 5rem;
		color: var(--text-1);
		text-decoration: none;
	}

	span {
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
	}

	button {
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

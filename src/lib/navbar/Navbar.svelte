<script>
    import HomeIcon from '$lib/navbar/images/home.svg';
    import RoadMapIcon from '$lib/navbar/images/roadmap.svg';
    import EducationIcon from '$lib/navbar/images/education.svg';
    import ProjectsIcon from '$lib/navbar/images/projects.svg';
    import ContactIcon from '$lib/navbar/images/contact.svg';
    import ExpandIcon from '$lib/navbar/images/expand.svg';
    import CollapseIcon from '$lib/navbar/images/collapse.svg';
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
    }

    const collapseNavbar = () => {
        if (!navbarCollapsed) {
            alternateNavbarState();
        }
    }

    onMount(() => {
        navbar.addEventListener('transitionend', (event) => {
            if (event.propertyName === 'width') {
                document.querySelectorAll('span').forEach(span => {
                    span.style.display = navbarCollapsed ? 'none' : 'block';
                });
            }
        });
        navbar.addEventListener('transitionstart', (event) => {
            if (event.propertyName === 'width' && navbarCollapsed) {
                document.querySelectorAll('span').forEach(span => {
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
			<a href="/home" on:click={collapseNavbar}>
                <img src={HomeIcon} alt="Home" />
				<span>HOME</span>
			</a>
		</li>
		<li>
			<a href="/roadmap" on:click={collapseNavbar}>
                <img src={RoadMapIcon} alt="Roadmap" />
				<span>ROADMAP</span>
			</a>
		</li>
		<li>
			<a href="/education" on:click={collapseNavbar}>
                <img src={EducationIcon} alt="Education" />
				<span>EDUCATION</span>
			</a>
		</li>
		<li>
			<a href="/projects" on:click={collapseNavbar}>
                <img src={ProjectsIcon} alt="Projects" />
				<span>PROJECTS</span>
			</a>
		</li>
		<li>
			<a href="/contact" on:click={collapseNavbar}>
                <img src={ContactIcon} alt="Contact" />
				<span>CONTACT</span>
			</a>
		</li>
		<li>
            <!-- svelte-ignore a11y-invalid-attribute -->
            <a href="#" on:click={alternateNavbarState}>
                <img src={navbarIcon} alt="Expand" />
            </a>
		</li>
	</ul>
</nav>
<div bind:this={coverBackground} class="cover-background" />

<style>
	nav {
		width: 5rem;
		height: 100vh;
		position: fixed;
        background-color: var(--bg-4);
        transition: width 0.150s;
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

    li img {
        width: 2rem;
        height: 100%;
        margin: 0 1.5rem;
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

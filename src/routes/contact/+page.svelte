<script>
	import LabelContact from '$lib/Labels/LabelContact.svelte';

	import LinkedInIcon from '$lib/Labels/icons/LinkedInIcon.svelte';
	import MailIcon from '$lib/Labels/icons/MailIcon.svelte';
	import GitHubIcon from '$lib/Labels/icons/GitHubIcon.svelte';

	const labelWidth = '190px';
	const spacerWidth = '26px';

	const links = {
		LinkedIn: 'https://www.linkedin.com/in/luis-reyero-fernandez/',
		Mail: 'mailto: luisreyero@hotmail.com',
		GitHub: 'https://github.com/Hakaary/'
	};
</script>

<main id="contact">
	<span id="contact-msg">Ways of <span id="contact-msg-span">contact...</span></span>
	<ul id="contact-list">
		<li class="contact-item">
			<LabelContact
				color="var(--bg-4)"
				label="LinkedIn"
				Icon={LinkedInIcon}
				width={labelWidth}
				iconSize="2.3rem"
				iconPaddingLeft="12px"
				{spacerWidth}
				link={links.LinkedIn}
			/>
		</li>
		<li class="contact-item">
			<LabelContact
				color="var(--bg-4)"
				label="Mail"
				Icon={MailIcon}
				width={labelWidth}
				iconSize="2.3rem"
				iconPaddingLeft="12px"
				{spacerWidth}
				link={links.Mail}
			/>
		</li>
		<li class="contact-item">
			<LabelContact
				color="var(--bg-4)"
				label="GitHub"
				Icon={GitHubIcon}
				width={labelWidth}
				iconSize="2.3rem"
				iconPaddingLeft="12px"
				{spacerWidth}
				link={links.GitHub}
			/>
		</li>
	</ul>
</main>

<style>
	#contact-msg {
		font-size: 40px;
		color: var(--text-1);
		margin-bottom: 60px;
	}

	#contact-msg-span {
		color: var(--text-3);
	}

	#contact {
		height: calc(100vh - 8rem);
		display: flex;
		flex-direction: column;
		padding-top: 6rem;
		align-items: center;
		transform: translateX(-2.2rem);
	}

	#contact-list {
		list-style-type: none;
		height: 360px;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
	}

	.contact-item {
		display: flex;
		align-items: center;
	}
</style>

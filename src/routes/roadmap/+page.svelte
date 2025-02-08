<script>
	import LabelYear from '$lib/Labels/LabelYear.svelte';
</script>

<main id="roadmap">
	<LabelYear color="var(--bg-2)" label="2015" />
	<LabelYear color="var(--bg-4)" label="2016" />
	<LabelYear color="var(--bg-2)" label="2017" />
	<LabelYear color="var(--bg-4)" label="2018" />
	<LabelYear color="var(--bg-2)" label="2019" />
	<LabelYear color="var(--bg-4)" label="2020" />
	<LabelYear color="var(--bg-2)" label="2021" />
</main>

<style>
	#roadmap {
		height: calc(100vh - 2rem);
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>

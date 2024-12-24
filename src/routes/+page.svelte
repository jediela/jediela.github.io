<script>
	import Footer from '$lib/components/Footer.svelte';
	import Me from '$lib/components/Me.svelte';
	import Experience from '$lib/components/Experience.svelte';
	import Projects from '$lib/components/Projects.svelte';
</script>

<Me />

<main class="flex flex-col items-center justify-center bg-blue-500 p-8 text-white">
	<div id="experience">
		<Experience />
	</div>
	<div id="projects">
		<Projects />
	</div>
</main>

<Footer />

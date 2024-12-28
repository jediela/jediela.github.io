<script>
	import { Separator } from '$lib/components/ui/separator/index.ts';
	import Footer from '$lib/components/Footer.svelte';
	import Me from '$lib/components/Me.svelte';
	import Experience from '$lib/components/Experience.svelte';
	import Projects from '$lib/components/Projects.svelte';
</script>

<Me />

<main class="flex flex-col items-center justify-center">
	<div id="experience">
		<Experience />
	</div>
	<Separator class="my-10" />
	<div id="projects">
		<Projects />
	</div>
</main>

<Footer />

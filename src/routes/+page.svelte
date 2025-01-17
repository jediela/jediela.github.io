<script>
	import { Separator } from '$lib/components/ui/separator';
	import Footer from '$lib/components/Footer.svelte';
	import Me from '$lib/components/Me.svelte';
	import Experience from '$lib/components/Experience.svelte';
	import Projects from '$lib/components/Projects.svelte';
	import Skills from '$lib/components/Skills.svelte';
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
	<Separator class="my-10" />
	<div id="skills">
		<Skills />
	</div>
</main>

<Footer />

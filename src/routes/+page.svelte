<script>
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import Me from '$lib/components/Me.svelte';
	import Experience from '$lib/components/Experience.svelte';
	import Projects from '$lib/components/Projects.svelte';
</script>

<Me />

<main class="bg-blue-500 p-4 text-white">
	<Experience />
	<Projects />
</main>

<Footer />

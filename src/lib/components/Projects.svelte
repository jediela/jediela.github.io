<script>
	import Card from './Card.svelte';
	import { Motion } from 'svelte-motion';
	import scriptoriumLogo from '../images/scriptorium.jpg';
	import svelte from '../images/svelte.png'
	import android from '../images/android.webp';
	import python from '../images/python.png';
	import weather from '../images/weather.jpg';
	import platformer from '../images/platformer.jpg';

	const projects = [
		{
			imageUrl: scriptoriumLogo,
			title: 'Scriptorium',
			description:
				'An online platform to write, execute, and share code, featuring blogs, comments, and voting. Built with Next.js.',
			buttonUrl: 'https://github.com/jediela/scriptorium'
		},
		{
			imageUrl: svelte,
			title: 'Portfolio Website',
			description:
				'Portfolio website showcasing my skills, projects, and professional experience. Built with SvelteKit and deployed on GitHub Pages.',
			buttonUrl: 'https://github.com/jediela/jediela.github.io'
		},
		{
			imageUrl: python,
			title: 'Markscope',
			description:
				'Mock course management platform with user authentication, role management, and data manipulation. Built with Flask.',
			buttonUrl: 'https://github.com/jediela/Markscope'
		},
		{
			imageUrl: android,
			title: 'ClickCraze',
			description:
				'A feature-rich Android shopping application designed for seamless user experience. Built with Java and integrated with Firebase.',
			buttonUrl: 'https://github.com/jediela/CSB07_Project'
		},
		{
			imageUrl: platformer,
			title: 'GUP',
			description:
				'A single-level 2D platformer game featuring simple gameplay mechanics. Built with Assembly.',
			buttonUrl: 'https://github.com/jediela/gup'
		},
		{
			imageUrl: weather,
			title: 'Weather Tracker',
			description:
				'An interactive website to explore real-time weather conditions for any location worldwide. Built with vanilla HTML, JavaScript, and CSS.',
			buttonUrl: 'https://github.com/jediela/Weather-app'
		}
	];
</script>

<h1 class="mb-8 text-center text-5xl font-semibold text-gray-800 dark:text-white">Projects</h1>
<div class="grid grid-cols-1 gap-x-5 gap-y-5 py-5 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-3">
	{#each projects as project}
		<Motion animate={{ opacity: 1 }} initial={{ opacity: 0 }}>
			<Card
				imageUrl={project.imageUrl}
				title={project.title}
				description={project.description}
				buttonUrl={project.buttonUrl}
			/>
		</Motion>
	{/each}
</div>

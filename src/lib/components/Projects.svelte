<script>
	// @ts-nocheck
	import * as Card from '$lib/components/ui/card/index.ts';
	import * as Carousel from '$lib/components/ui/carousel/index.ts';
	import CardComponent from './Card.svelte';
	import emblaCarouselSvelte from 'embla-carousel-svelte';
	import Autoplay from 'embla-carousel-autoplay';
	import { Motion } from 'svelte-motion';
	import scriptoriumLogo from '../images/scriptorium.jpg';
	import svelte from '../images/svelte.png';
	import android from '../images/android.webp';
	import python from '../images/python.png';
	import weather from '../images/weather.jpg';
	import platformer from '../images/platformer.jpg';
	import snfs from '../images/snfs.avif';
	import jaja from '../images/jaja.svg';

	const plugin = Autoplay({ delay: 2000, stopOnInteraction: true });

	const projects = [
		{
			imageUrl: jaja,
			title: 'Just a Job App',
			description:
				'Open-source application that automatically tracks your job applications by integrating with your inbox. Built with FastAPI and Next.js.',
			buttonUrl: 'https://www.justajob.app/'
		},
		{
			imageUrl: snfs,
			title: 'SNFS',
			description:
				'Web app that lets users create and manage investment portfolios and stock lists, view statistics, and share them with friends. Built with Flask and Next.js.',
			buttonUrl: 'https://github.com/jediela/SNFS'
		},
		{
			imageUrl: scriptoriumLogo,
			title: 'Scriptorium',
			description:
				'Online platform to write, execute, and share code, featuring blogs, comments, and voting. Built with Next.js.',
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
				'Feature-rich Android shopping application designed for seamless user experience. Built with Java and integrated with Firebase.',
			buttonUrl: 'https://github.com/jediela/CSB07_Project'
		},
		{
			imageUrl: platformer,
			title: 'GUP',
			description:
				'Single-level 2D platformer game featuring simple gameplay mechanics. Built with Assembly.',
			buttonUrl: 'https://github.com/jediela/gup'
		},
		{
			imageUrl: weather,
			title: 'Weather Tracker',
			description:
				'Interactive website to explore real-time weather conditions for any location worldwide. Built with vanilla HTML, JavaScript, and CSS.',
			buttonUrl: 'https://github.com/jediela/Weather-app'
		}
	];
</script>

<h1 class="mb-8 text-center text-5xl font-semibold text-gray-800 dark:text-white">Projects</h1>

<!-- <div class="grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
		{#each projects as project, i}
			<Motion
				initial={{ opacity: 0, y: 30 }}
				animate={{ opacity: 1, y: 0 }}
				transition={{ delay: i * 0.1, duration: 0.5 }}
			>
				<div
					class="transform rounded-2xl bg-white p-4 shadow-md transition-all duration-300 hover:-translate-y-2 hover:shadow-xl dark:bg-gray-800"
				>
					<Card
						imageUrl={project.imageUrl}
						title={project.title}
						description={project.description}
						buttonUrl={project.buttonUrl}
					/>
				</div>
			</Motion>
		{/each}
	</div> -->

<Carousel.Root
	class="mx-auto w-full max-w-6xl"
	opts={{
		align: 'start',
		loop: true
	}}
	plugins={[plugin]}
	on:mouseenter={plugin.stop}
	on:mouseleave={plugin.reset}
>
	<Carousel.Content class="px-1">
		{#each projects as project, i}
			<Carousel.Item class="basis-full md:basis-1/2 lg:basis-1/3">
				<Motion
					initial={{ opacity: 0, y: 20 }}
					animate={{ opacity: 1, y: 0 }}
					transition={{ delay: i * 0.1, duration: 0.5 }}
				>
						<CardComponent
							imageUrl={project.imageUrl}
							title={project.title}
							description={project.description}
							buttonUrl={project.buttonUrl}
						/>
				</Motion>
			</Carousel.Item>
		{/each}
	</Carousel.Content>

	<Carousel.Previous />
	<Carousel.Next />
</Carousel.Root>

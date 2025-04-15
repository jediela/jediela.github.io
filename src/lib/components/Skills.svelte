<script>
	import { BookOpen, CheckCircle } from 'lucide-svelte';

	let skills = [
		'React',
		'SvelteKit',
		'Angular',
		'Spring Boot',
		'Next.js',
		'Flask',
		'GitHub Actions',
		'Docker',
		'TailwindCSS',
		'JavaScript/TypeScript',
		'Python',
		'Java',
		'FastAPI',
		'HTML/CSS',
		'Assembly',
		'PostgreSQL'
	];
	let education = {
		institution: 'University of Toronto',
		years: '2021 - 2026',
		degree: 'Honours Bachelor of Science (HBSc) in Computer Science, with Co-op'
	};
</script>

<h1 class="mb-3 text-center text-5xl font-semibold text-gray-800 dark:text-white">
	Skills & Education
</h1>
<div class="mx-auto mb-5 max-w-6xl space-y-10 p-6">
	<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
		<div class="rounded-lg bg-white p-6 shadow-lg dark:bg-gray-800">
			<div class="mb-4 flex items-center space-x-4">
				<BookOpen class="h-6 w-6 text-blue-500 dark:text-blue-400" />
				<h3 class="text-xl font-semibold text-gray-900 dark:text-white">Education</h3>
			</div>
			<div class="space-y-2">
				<p class="text-lg font-bold text-gray-900 dark:text-white">{education.institution}</p>
				<p class="text-sm text-gray-700 dark:text-gray-400">{education.degree}</p>
				<p class="text-sm text-gray-700 dark:text-gray-400">{education.years}</p>
			</div>
		</div>
		<div class="rounded-lg bg-white p-6 shadow-lg dark:bg-gray-800">
			<div class="mb-4 flex items-center space-x-4">
				<CheckCircle class="h-6 w-6 text-green-500 dark:text-green-400" />
				<h3 class="text-xl font-semibold text-gray-900 dark:text-white">Skills</h3>
			</div>
			<div class="flex flex-wrap gap-3">
				{#each skills as skill}
					<span
						class="inline-block rounded-full bg-gray-100 px-4 py-2 text-sm font-medium text-gray-800 shadow-sm transition hover:bg-gray-200 dark:bg-gray-700 dark:text-gray-200 dark:hover:bg-gray-600"
					>
						{skill}
					</span>
				{/each}
			</div>
		</div>
	</div>
</div>

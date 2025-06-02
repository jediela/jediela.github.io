<script>
	let experiences = [
		{
			title: 'DevOps Engineer',
			company: 'Royal Bank of Canada, Global Asset Management (RBC GAM)',
			duration: 'May 2025 - Aug 2025',
			description: 'Helios on Actions.',
			skills: ['GitHub Actions', 'Jenkins']
		},
		{
			title: 'Software Developer',
			company: 'Royal Bank of Canada, Global Asset Management (RBC GAM)',
			duration: 'Sept 2024 - Dec 2024',
			description:
				'Worked on migrating application pipelines from Jenkins to GitHub Actions and updating front-end applications.',
			skills: ['GitHub Actions', 'Jenkins', 'Angular', 'Spring Boot']
		},
		{
			title: 'Software Developer',
			company: 'Ministry of Transportation of Ontario (MTO)',
			duration: 'Sept 2023 - Dec 2023',
			description: 'Developed the front-end pages and APIs for the TSOA complaint portal.',
			skills: ['Spring Boot', 'Angular', 'TypeScript', 'Java']
		}
	];
</script>

<h1 class="mb-12 mt-10 text-center text-5xl font-bold text-gray-800 dark:text-gray-200">
	Work Experience
</h1>

<div class="mx-auto max-w-6xl px-4">
	<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
		{#each experiences as experience}
			<div class="rounded-md border-l-4 border-blue-500 bg-white p-6 shadow-md dark:bg-gray-900">
				<h3 class="text-xl font-semibold text-gray-800 dark:text-white">{experience.title}</h3>
				<p class="text-sm text-gray-500 dark:text-gray-400">{experience.company}</p>
				<p class="mb-2 text-sm text-gray-400 dark:text-gray-500">{experience.duration}</p>

				<p class="text-gray-700 dark:text-gray-300">{experience.description}</p>
				<div class="mt-4">
					<p class="mb-1 font-semibold text-gray-700 dark:text-gray-400">Skills</p>
					<div class="flex flex-wrap gap-2">
						{#each experience.skills as skill}
							<span
								class="rounded bg-gray-100 px-2 py-1 text-sm text-gray-800 dark:bg-gray-700 dark:text-gray-200"
							>
								{skill}
							</span>
						{/each}
					</div>
				</div>
			</div>
		{/each}
	</div>
</div>

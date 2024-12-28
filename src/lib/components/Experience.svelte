<script>
	let experiences = [
		{
			title: 'Software Developer',
			company: 'Royal Bank of Canada (RBC)',
			duration: 'Sept 2024 - Dec 2024',
			description:
				'Worked on migrating application pipelines from Jenkins to GitHub Actions and updating front-end applications.',
			skills: ['GitHub Actions', 'Jenkins', 'Angular', 'Spring Boot']
		},
		{
			title: 'Software Developer',
			company: 'Ministry of Transportation of Ontario (MTO)',
			duration: 'Sept 2023 - Dec 2023',
			description:
				'Developed the front-end pages and APIs for the TSOA complaint portal.',
			skills: ['Spring Boot', 'Angular', 'TypeScript', 'Java']
		}
	];
</script>

<h1 class="mb-8 mt-10 text-center text-5xl font-semibold text-gray-800 dark:text-gray-200">Work Experience</h1>
  <div class="mx-auto max-w-6xl px-4">
	<div class="grid grid-cols-1 gap-8 sm:grid-cols-1 lg:grid-cols-2">
	  {#each experiences as experience}
		<div
		  class="transform rounded-lg bg-white p-6 shadow-lg transition-all hover:scale-105 hover:shadow-xl dark:bg-gray-800"
		>
		  <h3 class="text-xl font-semibold text-gray-800 dark:text-gray-200">{experience.title}</h3>
		  <p class="text-sm text-gray-500 dark:text-gray-400">{experience.company}</p>
		  <p class="mb-4 text-sm text-gray-400 dark:text-gray-500">{experience.duration}</p>
		  <p class="mb-4 text-gray-700 dark:text-gray-300">{experience.description}</p>
		  <div>
			<p class="font-semibold text-gray-600 dark:text-gray-400">Skills:</p>
			<ul class="list-disc pl-6 text-gray-700 dark:text-gray-300">
			  {#each experience.skills as skill}
				<li>{skill}</li>
			  {/each}
			</ul>
		  </div>
		</div>
	  {/each}
	</div>
  </div>

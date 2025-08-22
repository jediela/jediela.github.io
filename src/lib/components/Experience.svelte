<script>
	import {
		Timeline,
		TimelineItem,
		TimelineSeparator,
		TimelineDot,
		TimelineConnector,
		TimelineContent,
		TimelineOppositeContent
	} from 'svelte-vertical-timeline';

	import rbc from '../images/rbc.jpg';
	import mto from '../images/mto.jpeg';

	let experiences = [
		{
			title: 'DevOps Engineer',
			company: 'Royal Bank of Canada, Global Asset Management (RBC GAM)',
			logo: rbc,
			duration: 'May 2025 - Aug 2025',
			description: 'Managing and Optimizing CI/CD pipelines using GitHub Actions.',
			skills: ['GitHub Actions', 'Kubernetes', 'OpenShift', 'Bash', 'Docker']
		},
		{
			title: 'Software Developer',
			company: 'Royal Bank of Canada, Global Asset Management (RBC GAM)',
			logo: rbc,
			duration: 'Sept 2024 - Dec 2024',
			description:
				'Migrated application pipelines from Jenkins to GitHub Actions and updated front-end applications.',
			skills: ['GitHub Actions', 'Jenkins', 'Angular', 'Spring Boot']
		},
		{
			title: 'Software Developer',
			company: 'Ministry of Transportation of Ontario (MTO)',
			logo: mto,
			duration: 'Sept 2023 - Dec 2023',
			description: 'Developed the front-end pages and APIs for the TSOA complaint portal.',
			skills: ['Spring Boot', 'Angular', 'TypeScript', 'Java']
		}
	];
</script>

<h1 class="mb-12 mt-10 text-center text-5xl font-bold text-gray-800 dark:text-gray-200">
	Work Experience
</h1>

<Timeline position="alternate">
	{#each experiences as experience, i}
		<TimelineItem>
			<TimelineOppositeContent slot="opposite-content">
				<p class="text-lg font-semibold text-gray-500 dark:text-gray-400">
					{experience.duration}
				</p>
			</TimelineOppositeContent>

			<TimelineSeparator>
				<TimelineDot
					style="background-color: #3b82f6; height: 16px; width: 16px; border: 2px solid white; border-radius: 50%;"
				/>
				{#if i !== experiences.length - 1}
					<TimelineConnector style="background-color: #3b82f6;" />
				{/if}
			</TimelineSeparator>

			<TimelineContent>
				<div
					class="relative overflow-hidden rounded-xl border-l-4 bg-gradient-to-br from-white to-blue-50 p-8 pt-20
		       text-left shadow-lg transition-all
		       duration-300 ease-out hover:-translate-y-1 hover:shadow-2xl dark:from-gray-800
		       dark:to-gray-900"
					style="border-color: {i % 2 === 0 ? '#3b82f6' : '#f59e0b'};"
				>
					<div
						class="absolute left-6 top-1 flex h-16 w-16 items-center justify-center rounded-full border-2 border-white shadow-md"
					>
						<img
							src={experience.logo}
							alt={experience.company}
							class="h-14 w-14 rounded-full object-contain"
						/>
					</div>

					<div>
						<h3 class="text-2xl font-bold text-gray-800 dark:text-white">{experience.title}</h3>
						<p class="mb-2 text-base font-medium text-gray-600 dark:text-gray-400">
							{experience.company}
						</p>
						<p class="text-lg text-gray-700 dark:text-gray-300">{experience.description}</p>

						<div class="mt-4 flex flex-wrap gap-2">
							{#each experience.skills as skill}
								<span
									class="rounded-full bg-blue-100 px-4 py-1.5 text-sm font-medium text-blue-700
						        transition-colors duration-200 hover:bg-blue-200
						        dark:bg-blue-900 dark:text-blue-200 dark:hover:bg-blue-800"
								>
									{skill}
								</span>
							{/each}
						</div>
					</div>
				</div>
			</TimelineContent>
		</TimelineItem>
	{/each}
</Timeline>

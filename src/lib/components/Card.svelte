<script>
	import { Motion, useMotionTemplate, useMotionValue } from 'svelte-motion';

	export let imageUrl = '';
	export let title = '';
	export let description = '';
	export let buttonUrl = '';

	let mouseX = useMotionValue(0);
	let mouseY = useMotionValue(0);
	let background = useMotionTemplate`radial-gradient(200px circle at ${mouseX}px ${mouseY}px, rgba(51, 51, 51, 0.4), transparent 80%)`;
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div
	on:mousemove={(e) => {
		const { left, top } = e.currentTarget.getBoundingClientRect();
		mouseX.set(e.clientX - left);
		mouseY.set(e.clientY - top);
	}}
	class="group relative w-full max-w-[350px] overflow-hidden rounded-xl bg-neutral-950 bg-secondary"
>
	<div
		class="absolute right-5 top-0 h-px w-80 bg-gradient-to-l from-transparent via-white/30 via-10% to-transparent"
	></div>
	<Motion
		style={{
			background
		}}
		let:motion
	>
		<div
			use:motion
			class="pointer-events-none absolute -inset-px rounded-xl opacity-0 transition duration-300 group-hover:opacity-100"
		></div>
	</Motion>
	<div class="relative flex flex-col gap-3 rounded-xl border bg-secondary px-4 py-5">
		<div class="space-y-2">
			<!-- svelte-ignore a11y_img_redundant_alt -->
			<img src={imageUrl} alt="Logo" class="h-52 w-full rounded-xl object-cover" />
			<div class="flex flex-row items-center justify-between pt-2">
				<h3 class="text-xl font-semibold text-primary">{title}</h3>
			</div>
			<p class="pb-3 text-sm leading-[1.5] text-primary">{description}</p>
			<a
				href={buttonUrl}
				class="hover:bg-primary-700 hover:text-primary-100 inline-flex w-full items-center justify-center gap-1 rounded-lg bg-primary px-4 py-3 text-sm font-semibold text-secondary duration-300 hover:scale-105 hover:shadow-lg"
				aria-label="view project"
			>
				View Project
			</a>
		</div>
	</div>
</div>

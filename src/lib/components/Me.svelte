<script>
	import BlurIn from './BlurIn.svelte';
	import { Home, NotepadTextIcon, CodeIcon, WorkflowIcon, Sun, Moon } from 'lucide-svelte';
	import GithubSvg from '$lib/svg/github.svg';
	import LinkedInSvg from '$lib/svg/linkedin.svg';
	import * as Tooltip from '$lib/components/ui/tooltip';
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import Dock from './Dock.svelte';
	import DockIcon from './DockIcon.svelte';
	import { mode, setMode } from 'mode-watcher';

	let navs = {
		navbar: [
			{ label: 'Home', icon: Home, href: '#' },
			{ label: 'My Resume', icon: NotepadTextIcon, href: '#' },
			{ label: 'Experience', icon: WorkflowIcon, href: '#experience' },
			{ label: 'Projects', icon: CodeIcon, href: '#projects' }
		],
		contact: [
			{ label: 'Github', icon: GithubSvg, href: 'https://github.com/jediela' },
			{
				label: 'LinkedIn',
				icon: LinkedInSvg,
				href: 'https://www.linkedin.com/in/jediel-antalan/'
			}
		]
	};

	function handleModeChange() {
		if ($mode === 'light') {
			setMode('dark');
		} else {
			setMode('light');
		}
	}

	// @ts-ignore
	function handleAnchorClick(event) {
		event.preventDefault();
		const link = event.currentTarget;
		const anchorId = new URL(link.href).hash.replace('#', '');
		const anchor = document.getElementById(anchorId);
		if (anchor) {
			window.scrollTo({
				top: anchor.offsetTop,
				behavior: 'smooth'
			});
		}
	}
</script>

<div
	class="relative flex h-[500px] w-full flex-col items-center justify-center overflow-hidden rounded-lg border bg-gradient-to-b from-transparent via-background to-transparent md:shadow-xl"
>
	<BlurIn
		class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-5xl font-semibold leading-none text-transparent dark:from-white dark:to-slate-900/10 md:text-8xl"
		word="Hi! I'm Jed 👋"
	/>
	<div class="sticky top-0 flex justify-center bg-background">
		<Dock direction="middle" class="relative" let:mouseX let:distance let:magnification>
			{#each navs.navbar as item}
				<DockIcon {mouseX} {magnification} {distance}>
					<Tooltip.Root>
						<a href={item.href} on:click={handleAnchorClick} class="navbar-link">
							<Tooltip.Trigger
								class="mx-0 rounded-full p-3 transition-all duration-200 hover:bg-zinc-900/80"
							>
								<svelte:component this={item.icon} size={22} strokeWidth={1.2} />
							</Tooltip.Trigger>
							<Tooltip.Content sideOffset={8}>
								<p>{item.label}</p>
							</Tooltip.Content>
						</a></Tooltip.Root
					>
				</DockIcon>
			{/each}
			<Separator orientation="vertical" class="h-full w-[0.6px]" />
			{#each navs.contact as item}
				<DockIcon {mouseX} {magnification} {distance}>
					<Tooltip.Root>
						<a href={item.href} class="no-underline">
							<Tooltip.Trigger
								class="rounded-full transition-all duration-200 hover:bg-zinc-900/80"
							>
								<img src={item.icon} alt={item.label} class="m-3 h-5 w-5" />
							</Tooltip.Trigger>
							<Tooltip.Content sideOffset={9}>
								<p>{item.label}</p>
							</Tooltip.Content>
						</a></Tooltip.Root
					>
				</DockIcon>
			{/each}
			<Separator orientation="vertical" class="h-full w-[0.6px]" />
			<DockIcon {mouseX} {magnification} {distance}>
				<Tooltip.Root>
					<Tooltip.Trigger>
						<button
							class="rounded-full p-3 transition-all duration-200 hover:bg-zinc-900/80"
							on:click={handleModeChange}
							aria-label="Toggle theme"
						>
							{#if $mode === 'light'}
								<Moon class="h-[1.2rem] w-[1.2rem]" />
							{:else}
								<Sun class="h-[1.2rem] w-[1.2rem]" />
							{/if}
						</button>
					</Tooltip.Trigger>
					<Tooltip.Content sideOffset={9}>
						<p>Toggle theme</p>
					</Tooltip.Content>
				</Tooltip.Root>
			</DockIcon>
		</Dock>
	</div>
</div>

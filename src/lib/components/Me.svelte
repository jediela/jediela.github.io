<script>
	import BlurIn from './BlurIn.svelte';
	import { Home, NotepadTextIcon, CodeIcon, Briefcase, Sun, Moon, School } from 'lucide-svelte';
	import GithubSvg from '$lib/svg/github.svg';
	import GitHubDarkSvg from '$lib/svg/github-dark.svg';
	import LinkedInSvg from '$lib/svg/linkedin.svg';
	import LinkedInDarkSvg from '$lib/svg/linkedin-dark.svg';
	import * as Tooltip from '$lib/components/ui/tooltip';
	import Separator from '$lib/components/ui/separator/separator.svelte';
	import Dock from './Dock.svelte';
	import DockIcon from './DockIcon.svelte';
	import { mode, setMode } from 'mode-watcher';

	let navs = {
		navbar: [
			{ label: 'Home', icon: Home, href: '#' },
			{
				label: 'My Resume',
				icon: NotepadTextIcon,
				href: 'Jediel_Antalan_Resume.pdf',
				target: '_blank'
			},
			{ label: 'Experience', icon: Briefcase, href: '#experience' },
			{ label: 'Projects', icon: CodeIcon, href: '#projects' },
			{ label: 'Skills & Education', icon: School, href: '#skills' }
		],
		contact: [
			{
				label: 'Github',
				icon: GithubSvg,
				darkIcon: GitHubDarkSvg,
				href: 'https://github.com/jediela'
			},
			{
				label: 'LinkedIn',
				icon: LinkedInSvg,
				darkIcon: LinkedInDarkSvg,
				href: 'https://www.linkedin.com/in/jediel-antalan/'
			}
		]
	};

	function handleModeChange() {
		setMode($mode === 'light' ? 'dark' : 'light');
	}

	// @ts-ignore
	function handleAnchorClick(event) {
		event.preventDefault();
		const link = event.currentTarget;
		const href = link.href;

		if (href.endsWith('.pdf')) {
			window.open(href, '_blank');
			return;
		}

		const anchorId = new URL(href).hash.replace('#', '');
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
	class="relative flex h-screen w-full flex-col items-center justify-center overflow-hidden rounded-lg border bg-gradient-to-b from-transparent via-background to-transparent md:shadow-xl"
>
	<BlurIn
		class="pointer-events-none whitespace-pre-wrap bg-gradient-to-b from-black to-gray-300/80 bg-clip-text text-center text-5xl font-semibold leading-none text-transparent dark:from-white dark:to-slate-900/10 md:text-8xl"
		word="Hi! I'm"
		name="Jed Antalan"
	/>
	<div class="flex justify-center bg-background">
		<Dock direction="middle" class="relative" let:mouseX let:distance let:magnification>
			{#each navs.navbar as item}
				<DockIcon {mouseX} {magnification} {distance}>
					<Tooltip.Root>
						<a
							href={item.href}
							target={item.target}
							on:click={handleAnchorClick}
							class="navbar-link"
						>
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
						<a href={item.href} class="no-underline" target="_blank">
							<Tooltip.Trigger
								class="rounded-full transition-all duration-200 hover:bg-zinc-900/80"
							>
								<img
									src={$mode === 'light' ? item.icon : item.darkIcon}
									alt={item.label}
									class="m-3 h-5 w-5"
								/>
							</Tooltip.Trigger>
							<Tooltip.Content sideOffset={9}>
								<p>{item.label}</p>
							</Tooltip.Content>
						</a>
					</Tooltip.Root>
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

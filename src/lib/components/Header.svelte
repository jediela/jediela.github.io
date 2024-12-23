<script lang="ts">
	import Sun from 'lucide-svelte/icons/sun';
	import Moon from 'lucide-svelte/icons/moon';
	import { mode, setMode } from 'mode-watcher';
	import { Button } from '$lib/components/ui/button/index.js';

	function handleModeChange() {
		if ($mode === 'light') {
			setMode('dark');
		} else {
			setMode('light');
		}
	}
</script>

<header class="sticky top-0 z-50">
	<Button on:click={handleModeChange} variant="outline" size="icon">
		{#if $mode === 'light'}
			<Moon class="h-[1.2rem] w-[1.2rem]" />
		{:else}
			<Sun class="h-[1.2rem] w-[1.2rem]" />
		{/if}
		<span class="sr-only">Toggle theme</span>
	</Button>

	<p>Current mode: {$mode}</p>
</header>

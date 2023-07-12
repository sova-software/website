<script lang="ts">
	//  -> Imports
	import { RadioGroup, RadioItem, TabAnchor, TabGroup } from '@skeletonlabs/skeleton';

	//  -> Local imports
	import { scrollStore } from '$lib/stores';
	import { page } from '$app/stores';
</script>

<nav
	class="z-[999] p-2 flex items-center transition-colors duration-300 variant-ghost-surface variant-glass-surface mx-auto w-fit gap-2 rounded-token fixed left-4 right-4 bottom-4 md:bottom-auto md:left-4 md:right-4 md:top-4"
>
	<a href="/" class="w-20">
		<img src="/img/sova.svg" alt="Sova logo" />
	</a>
	<TabGroup
		active="variant-soft-primary"
		rounded="rounded-token"
		space="space-x-1"
		class="bg-surface-200-700-token border-token border-surface-400-500-token rounded-token p-1"
		border=""
	>
		<TabAnchor href="/" selected={$page.url.pathname === '/'}>Home</TabAnchor>
		<TabAnchor href="/projects" selected={$page.url.pathname === '/projects'}>Projects</TabAnchor>
		<TabAnchor href="/about" selected={$page.url.pathname === '/about'}>About</TabAnchor>
	</TabGroup>
</nav>

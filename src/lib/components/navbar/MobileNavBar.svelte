<script lang="ts">
	//  -> Imports
	import { RadioGroup, RadioItem } from '@skeletonlabs/skeleton';
	import { goto } from '$app/navigation';
	import { browser } from '$app/environment';

	//  -> Internal Variables
	let tab = '/';

	//  -> Reactivity
	$: if (browser) goto(tab);
</script>

<nav class="md:hidden sticky bottom-0 p-2 flex items-center transition-colors duration-300 variant-glass-surface">
	<a href="/">
		<img src="/s.svg" alt="Sova logo" />
	</a>
	<RadioGroup class="ml-auto" fill="variant-filled-primary">
		<RadioItem bind:group={tab} name="justify" value="/">Sova</RadioItem>
		<RadioItem bind:group={tab} name="justify" value="/projects">Projects</RadioItem>
		<RadioItem bind:group={tab} name="justify" value="/about">About</RadioItem>
	</RadioGroup>
</nav>

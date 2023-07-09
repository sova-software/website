<script lang="ts">
	//  -> Imports
	import { RadioGroup, RadioItem } from '@skeletonlabs/skeleton';

	//  -> Local imports
	import { scrollStore } from '$lib/stores';

	//  -> Internal Variables
	let tab = '/';
</script>

<nav class="sticky top-0 p-8 grid grid-cols-3 items-center transition-colors duration-300 {$scrollStore.y > 0 ? 'variant-glass-surface' : ''}">
	<img src="/sova.svg" alt="Sova logo" />
	<RadioGroup class="mx-auto" fill="variant-filled-primary">
		<RadioItem bind:group={tab} name="justify" value="/">(label)</RadioItem>
		<RadioItem bind:group={tab} name="justify" value="/projects">(label)</RadioItem>
		<RadioItem bind:group={tab} name="justify" value="/about">(label)</RadioItem>
	</RadioGroup>
</nav>

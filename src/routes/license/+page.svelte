<script lang="ts">
	//  -> Imports
	import { Accordion, AccordionItem, ProgressRadial } from '@skeletonlabs/skeleton';
	import { onMount } from 'svelte';
	import { blur } from 'svelte/transition';

	//  -> Variables
	let open = 0;
	let fileData: {
		name: string;
		author: string;
		usage: string[];
		license: string;
		originates: string;
		type: string;
	}[] = [];
	let promFileData: Promise<Response>;

	//  -> Mount
	onMount(() => {
		promFileData = fetch('/data/credits.json');
		promFileData.then(async (res) => (fileData = await res.json()));
	});
</script>

<div class="mx-auto max-w-xl flex flex-col gap-4">
	<h1 class="h1 text-center">Here's the legal stuff</h1>

	<Accordion autocollapse>
		{#await promFileData}
			<div class="flex justify-center items-center gap-2 p-4">
				<ProgressRadial width="w-12" stroke={100} />
			</div>
		{:then}
			{#each fileData as { name, author, usage, license, originates, type }, i}
				<div in:blur={{ delay: 100 * i }}>
					<AccordionItem
						class="variant-ghost-surface card"
						hover="hover:bg-primary-hover-token {open === i
							? 'bg-surface-active-token !rounded-b-none'
							: ''}"
						open={open === i}
						on:toggle:click={(e) => {
							if (e.detail.open) open = i;
						}}
					>
						<svelte:fragment slot="summary">{type}: {name} ({usage.join(', ')})</svelte:fragment>
						<svelte:fragment slot="content">
							This {type} is used within this website. All rights belong to the original author, {author}.
							<a class="anchor" href={license}>The license of this {type} can be found here</a>,
							according to
							<a class="anchor" href={originates}>this source</a>.
						</svelte:fragment>
					</AccordionItem>
				</div>
			{/each}
		{/await}
	</Accordion>
</div>

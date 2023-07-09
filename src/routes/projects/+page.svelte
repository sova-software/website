<script lang="ts">
	//  -> Imports
	import { ProgressRadial } from '@skeletonlabs/skeleton';
	import { onMount } from 'svelte';

	//  -> Variables
	let fileData: {
		title: string;
		description: string;
		tags: string[];
		image: string;
		imgAlt: string;
		buttons: {
			label: string;
			href: string;
		}[];
		bg: string;
	}[] = [];
	let promFileData: Promise<Response>;

	//  -> Mount
	onMount(() => {
		promFileData = fetch('/data/projects.json');
		promFileData.then(async (res) => (fileData = await res.json()));
	});
</script>

{#await promFileData}
	<div class="flex justify-center items-center gap-2 p-4">
		<ProgressRadial width="w-12" stroke={100} />
	</div>
{:then}
	{#each fileData as { title, description, tags, image, imgAlt, buttons, bg }, i}
		<section class="mx-auto grid max-w-screen-xl gap-8 md:grid-cols-2 lg:grid-cols-3 p-2 my-4 shadow-lg rounded-container-token" style="background-color: {bg};">
			{#if !(i % 2)}
				<img alt={imgAlt} src={image} width="720" height="600" />
			{/if}
			<div class="flex flex-col items-center md:items-start lg:col-span-2">
				<h2 class="h2">{title}</h2>

				<p class="mt-2 text-sm text-gray-400">
					{description}
				</p>

				<div class="mt-4 flex gap-4">
					{#each buttons as { label, href }, i}
						<a class="btn {i === 0 ? 'variant-filled-primary' : 'variant-ghost-secondary'}" {href}>{label}</a>
					{/each}
				</div>
			</div>

			{#if i % 2}
				<img alt={imgAlt} src={image} width="720" height="600" />
			{/if}
		</section>
	{/each}
{/await}

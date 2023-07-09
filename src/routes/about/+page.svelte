<script lang="ts">
	//  -> Imports
	import { Avatar, ProgressRadial } from '@skeletonlabs/skeleton';
	import { onMount } from 'svelte';
	import { blur } from 'svelte/transition';

	//  -> Variables
	let fileData: {
		name: string;
		username: string;
		image: string;
		buttons: {
			label: string;
			href: string;
		}[];
	}[] = [];
	let promFileData: Promise<Response>;

	//  -> Mount
	onMount(() => {
		promFileData = fetch('/data/devs.json');
		promFileData.then(async (res) => (fileData = await res.json()));
	});
</script>

{#await promFileData}
	<div class="flex justify-center items-center gap-2 p-4">
		<ProgressRadial width="w-12" stroke={100} />
	</div>
{:then}
<div class="grid gap-4 md:grid-cols-2 lg:grid-cols-3 mx-auto">
	{#each fileData as { name, username, image, buttons }, i}
		<section class="flex max-w-screen-xl gap-4 p-4 shadow-lg rounded-container-token variant-ghost-surface" in:blur={{ delay: 100 * i }}>
			<Avatar alt="{name}s profile picture" src={image} width="w-16 h-16"  />

			<div class="flex flex-col items-center md:items-start lg:col-span-2">
				<h2 class="h2">{name}</h2>

				<p class="mt-2 text-sm text-gray-400">
					@{username}
				</p>

				<div class="mt-4 flex gap-4">
					{#each buttons as { label, href }, i}
						<a class="btn {i === 0 ? 'variant-filled-primary' : 'variant-ghost-primary'}" {href}>{label}</a>
					{/each}
				</div>
			</div>
		</section>
	{/each}
	</div>
{/await}

<script lang="ts">
	//  -> Imports
	import { onMount } from 'svelte';
	import { blur } from 'svelte/transition';

	//  -> Variables
	let hidden = true;

	//  -> Mount
	onMount(() => {
		hidden = false;
	});
</script>

{#if !hidden}
	<div class="container h-full mx-auto flex flex-col p-8 items-center gap-4">
		<h1 class="h1" in:blur={{ delay: 100 }}>Hey there!</h1>
		<p class="text-justify" in:blur={{ delay: 200 }}>
			Sova is a technology company. Our goal is to make the world better. We're primarily focused on
			making software, specifically for desktop. Cool, eh?
		</p>
		<a class="btn variant-filled-primary" href="/projects" in:blur={{ delay: 300 }}>
			Check out our projects
		</a>
	</div>
{/if}

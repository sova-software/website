<script lang="ts">
	//  -> CSS imports
	import '../theme.css';
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	import '../app.postcss';

	//  -> Imports
	import { AppShell } from '@skeletonlabs/skeleton';

	//  -> Local imports
	import { scrollStore } from '$lib/stores';
	import Footer from '$lib/components/footer/Footer.svelte';
	import NavBar from '$lib/components/navbar/NavBar.svelte';
</script>

<svelte:head>
	<title>Sova</title>
</svelte:head>

<AppShell
	on:scroll={(e) => {
		scrollStore.set({
			x: e.currentTarget.scrollLeft,
			y: e.currentTarget.scrollTop
		});
	}}
>
	<!-- (header) -->
	<!-- (sidebarLeft) -->
	<!-- (sidebarRight) -->
	<!-- (pageHeader) -->
	<!-- Router Slot -->
	<div class="p-4 min-h-screen md:pt-24">
		<slot />
	</div>
	<NavBar />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter">
		<footer class="pb-24 md:pb-4 p-4 bg-surface-900">
			<Footer />
		</footer>
	</svelte:fragment>
	<!-- (footer) -->
</AppShell>

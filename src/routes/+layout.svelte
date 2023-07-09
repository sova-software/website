<script lang="ts">
	//  -> CSS imports
	import '../theme.css';
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	import '../app.postcss';

	//  -> Imports
	import { AppShell } from '@skeletonlabs/skeleton';

	//  -> Local imports
	import DesktopNavBar from '$lib/components/navbar/DesktopNavBar.svelte';
	import { scrollStore } from '$lib/stores';
</script>

<AppShell on:scroll={(e) => {
	scrollStore.set({
		x: e.currentTarget.scrollLeft,
		y: e.currentTarget.scrollTop
	});
}}>
	<svelte:fragment slot="header">
		<DesktopNavBar />
	</svelte:fragment>
	<!-- (sidebarLeft) -->
	<!-- (sidebarRight) -->
	<!-- (pageHeader) -->
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter">Page Footer</svelte:fragment>
	<!-- (footer) -->
</AppShell>

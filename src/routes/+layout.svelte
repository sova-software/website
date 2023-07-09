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
	import MobileNavBar from '$lib/components/navbar/MobileNavBar.svelte';
</script>

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
	<DesktopNavBar />
	<div class="p-4">
		<slot />
	</div>
	<MobileNavBar />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter">Page Footer</svelte:fragment>
	<!-- (footer) -->
</AppShell>

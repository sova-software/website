<script lang="ts">
	//  -> Local imports
	import { page } from '$app/stores';
</script>

<div class="flex justify-center items-center gap-2 p-4">
	<img alt="Error {$page.status}" src="https://http.cat/{$page.status}" width="720" />
</div>
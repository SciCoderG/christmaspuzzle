<script lang="ts">
	import Raetsel from '$lib/Raetsel.svelte';
	import type { PageData } from './$types';

	export let data: PageData;
</script>

<svelte:head>
    <title>Jasmin's Weihnachtsrätsel</title>
</svelte:head>
<Raetsel />

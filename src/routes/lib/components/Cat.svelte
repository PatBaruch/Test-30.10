<script>
	import { getContext, onMount } from 'svelte';
	export let catId;

	let data = [];
	let loading = true;
	let error = null;
	const apiUrl = `${getContext('apiReference').mainUrl}${catId}`;
	console.log(apiUrl);
	// Fetching data on component mount
	onMount(async () => {
		try {
			const response = await fetch(apiUrl);
			if (!response.ok) {
				throw new Error('Failed to fetch data');
			}
			data = await response.json();
		} catch (err) {
			error = err.message;
		} finally {
			loading = false;
		}
	});
</script>

<!-- Loading state -->
{#if loading}
	<p>Loading...</p>
{/if}

<!-- Error state -->
{#if error}
	<p>Error: {error}</p>
{/if}

<!-- Render data when available -->
{#if !loading && !error && data.type === 'Cat'}
	<div class="appointment cursor-pointer" id={data.id}>
		<ul class="flex flex-wrap justify-between bg-slate-100 rounded-lg">
			<li class="bg-slate-100 mr-2 p-2 rounded-l-lg">{data.id} {data.name} {data.type}</li>
		</ul>
	</div>
{/if}

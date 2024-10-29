<script>
	import CatList from './lib/components/CatList.svelte';
	import Cat from './lib/components/Cat.svelte';
	import { setContext } from 'svelte';

	setContext('apiReference', {
		mainUrl: 'http://localhost:3010'
	});
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="container w-full mx-auto">
	<section class="mt-10">
		<h2 class="text-6xl">
			<span class="inline-block bg-pink-500 rounded-lg p-2">Cat List</span>
		</h2>
	</section>
	<section class="flex flex-col lg:flex-row mt-5">
		<div class="basis-4/6 bg-slate-50 rounded-lg p-10 lg:mr-8">
			<CatList />
		</div>
	</section>
</div>

<style>
</style>

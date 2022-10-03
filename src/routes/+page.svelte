<script lang="ts">
	import type HeroCubeSvelte from '$lib/components/HeroCube.svelte';
	import { onMount } from 'svelte';
	let Cube: HeroCubeSvelte;

	// import HeroCube from "$lib/components/HeroCube.svelte";

	onMount(async () => {
		const mod = await import('$lib/components/HeroCube.svelte');
		Cube = mod.default;
	});
</script>

<div class="min-h-[calc(100vh-calc(4rem))] flex flex-col lg:flex-row bg-black" id="hero">
	<div id="hero-half" class="flex-grow-[2] flex flex-col" > <span class="mt-auto lg:-mb-10 lg:ml-32 mx-auto lg:text-[10rem] text-[5rem] lg:[line-height=9.5rem] text-white">SYNERGY</span><span class="mt-2 mx-auto lg:ml-32 lg:mb-36 text-white text-4xl">TEXT HERE</span></div>
	<div id="hero-cube" class="flex-grow flex justify-center items-center"><svelte:component this={Cube} /></div>
</div>
<div id="events" />
<div id="faq" />
<div id="about" />
<div id="contact-us" />

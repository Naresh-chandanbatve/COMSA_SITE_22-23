<script lang="ts">
	import Faq from '$lib/components/FAQPageDesktop.svelte';
	import DesktopHero from '$lib/assets/desktop-alt.jpg';
	import { page_1, page_1_title } from '$lib/data/FAQs';
	import { onMount, SvelteComponent } from 'svelte';
	import { goto } from '$app/navigation';
	import AboutUs from '$lib/components/AboutUs.svelte';
	import EventCard from '$lib/components/EventCard.svelte';
	let innerWidth: number;
	let innerHeight: number;
	// Should have been SvelteComponent
	let Cube: any;
	onMount(async () => {
		if (innerWidth < 1024) await goto('/m/');
		const mod = await import('$lib/components/HeroCubeDesktop.svelte');
		Cube = mod.default;
	});
</script>

<svelte:window bind:innerWidth bind:innerHeight />

<div
	style="--bg-url: url({DesktopHero});"
	class="hero-bg min-h-[calc(100vh-calc(4rem))] flex flex-col lg:flex-row bg-base-100 overflow-x-hidden mt-16 scroll-mt-16"
	id="hero"
>
	<div id="hero-half" class="flex-grow-[2] flex flex-col">
		<span
			class="mt-auto mb-4 xl:mb-10 xl:ml-16 2xl:ml-32 mx-auto text-4xl 2xl:text-[10rem]  xl:text-[5rem] xl:[line-height=9.5rem] text-base-content vimh"
			>SYNERGY</span
		><span
			class="mt-2 mx-auto xl:ml-16 2xl:ml-32 lg:mb-36 text-base-content text-xl xl:text-2xl 2xl:text-4xl"
			>TEXT HERE</span
		>
	</div>
	<div id="hero-cube" class="flex-grow flex justify-center items-center">
		<svelte:component this={Cube} />
	</div>
</div>
<div class="flex flex-wrap px-36 justify-evenly items-center gap-8 bg-gradient-to-b content-gradient" id="content">
	<div class="mt-10 w-5/6 flex flex-row flex-wrap justify-evenly align-middle gap-10">
		<h1 class="text-4xl text-center text-base-content w-screen vimh">EVENTS</h1>
		<EventCard />
		<EventCard />
		<EventCard />
		<EventCard />
		<EventCard />
		<EventCard />
		<EventCard />
		<EventCard />
	</div>
	<div class=" mt-10 w-5/6 flex flex-row flex-wrap justify-evenly align-middle">
		<div class="w-5/6"><Faq data_list={page_1} title={page_1_title} /></div>
	</div>
	<div class=" mt-10 w-5/6 flex flex-row flex-wrap justify-evenly align-middle">
	<AboutUs />
	</div>
</div>

<style lang="postcss">
	.hero-bg {
		background: no-repeat right;
		background-image: linear-gradient(#00000050, #000000dd), var(--bg-url);
		background-blend-mode: multiply, normal;
		background-size: cover;
	}

	.content-gradient {
		/* --tw-gradient-stops: #0000004D, theme('colors.sky.400'), theme('colors.rose.400'), theme('colors.lime.400'); */
		background: linear-gradient(to top, rgb(29, 78, 216), rgb(30, 64, 175), rgb(17, 24, 39));
	}
</style>

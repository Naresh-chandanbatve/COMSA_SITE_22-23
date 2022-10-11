<script lang="ts">
	import Faq from '$lib/components/FAQPageMobile.svelte';
	import MobileHero from '$lib/assets/mobile-hero.jpg';
	import {page_0, page_0_title, page_1, page_1_title, page_2, page_2_title} from '$lib/data/FAQs'
import { onMount, SvelteComponent } from 'svelte';
	// Should have been SvelteComponent 
	let Cube: any;
	let is_landscape: boolean = false; // mobile first shite
	onMount(async () => {
			const mod = await import('$lib/components/HeroCubeMobile.svelte');
			Cube = mod.default;
	});
</script>


<div style="--bg-url: url({MobileHero});" class="hero-bg min-h-[calc(100vh-calc(4rem))] flex flex-col lg:flex-row bg-base-100 snap-end overflow-x-hidden mt-16 scroll-mt-16" id="hero">
	<div id="hero-half" class="mt-10 flex flex-col">
		<span
			class="mt-auto lg:-mb-10 lg:ml-32 mx-auto lg:text-[10rem] text-[5rem] lg:[line-height=9.5rem] text-base-content"
			>SYNERGY</span
		><span class="mt-2 mx-auto lg:ml-32 lg:mb-36 text-base-content text-4xl">TEXT HERE</span>
	</div>
	<div id="hero-cube" class="flex-grow flex justify-center items-center">
		<svelte:component this={Cube} />
	</div>
</div>
<div class="min-h-[calc(100vh-calc(4rem))]  snap-end bg-red-500" id="events" >
</div>


<div class="min-h-[calc(100vh-calc(4rem))] snap-end bg-orange-500" id="faq" >
	<Faq data_list={page_1} title="{page_1_title}"/>
</div>

<div class="min-h-[calc(100vh-calc(4rem))]  snap-end bg-green-500" id="about" />
<div class="min-h-[calc(100vh-calc(4rem))]  snap-end bg-purple-500" id="contact-us" />


<style>
	.hero-bg {
		background: var(--bg-url) no-repeat top;
        background-size: cover;
	}
</style>
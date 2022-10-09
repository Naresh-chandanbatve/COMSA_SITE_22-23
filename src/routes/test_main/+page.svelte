<script lang="ts">
	import type HeroCubeSvelte from '$lib/components/HeroCubeDesktop.svelte';
	import { onMount } from 'svelte';
	let Cube: HeroCubeSvelte;

	// import HeroCube from "_clib/components/HeroCube.svelte";

	let c: HTMLCanvasElement;
	let _c: CanvasRenderingContext2D;

	var col = function (x:number, y:number, r:number, g:number, b:number) {
		_c.fillStyle = 'rgb(' + r + ',' + g + ',' + b + ')';
		_c.fillRect(x, y, 1, 1);
	};
	var R = function (x: number, y:number, t:number) {
		return Math.floor(192 + 64 * Math.cos((x * x - y * y) / 300 + t));
	};

	var G = function (x: number, y:number, t:number) {
		return Math.floor(
			192 + 64 * Math.sin((x * x * Math.cos(t / 4) + y * y * Math.sin(t / 3)) / 300)
		);
	};

	var B = function (x: number, y:number, t:number) {
		return Math.floor(
			192 +
				64 * Math.sin(5 * Math.sin(t / 9) + ((x - 100) * (x - 100) + (y - 100) * (y - 100)) / 1100)
		);
	};

	var t = 0;

	onMount(async () => {
		const mod = await import('$lib/components/HeroCubeDesktop.svelte');
		Cube = mod.default;

		_c = c.getContext('2d');

		var run = function () {
			for (let x = 0; x <= 35; x++) {
				for (let y = 0; y <= 35; y++) {
					col(x, y, R(x, y, t), G(x, y, t), B(x, y, t));
				}
			}
			t = t + 0.01;
			window.requestAnimationFrame(run);
		};
		run();
	});
</script>

<canvas id="canv" width="32" height="32" class="fixed top-0 left-0 w-full h-full -z-50" bind:this={c} />

<div class="min-h-[calc(100vh-calc(4rem))] flex flex-col lg:flex-row bg-transparent z-10" id="hero">
	<div id="hero-half" class="flex-grow-[2] flex flex-col">
		<span
			class="mt-auto lg:-mb-10 lg:ml-32 mx-auto lg:text-[10rem] text-[5rem] lg:[line-height=9.5rem] text-black"
			>SYNERGY</span
		><span class="mt-2 mx-auto lg:ml-32 lg:mb-36 text-black text-4xl">TEXT HERE</span>
	</div>
	<div id="hero-cube" class="flex-grow flex justify-center items-center">
		<svelte:component this={Cube} />
	</div>
</div>
<div id="events" />
<div id="faq" />
<div id="about" />
<div id="contact-us" />

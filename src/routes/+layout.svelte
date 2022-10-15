<script>
	import '../app.postcss';
	import "iconify-icon";
	import { Modals, closeModal } from 'svelte-modals'
	import {fade} from 'svelte/transition'
</script>

<Modals>
	<div
	  slot="backdrop"
	  class="backdrop z-[100]"
	  transition:fade
	  on:click={closeModal}
	/>
  </Modals>


<div class="drawer">
	<input id="side-drawer" type="checkbox" class="drawer-toggle" />
	<div class="drawer-content scroll-smooth snap-y snap-mandatory snap-always scroll-m-16 flex flex-col">
		<!-- Navbar -->
		<div class="w-full navbar fixed top-0 left-0 bg-base-300 z-50">
			<div class="flex-none lg:hidden">
				<label for="side-drawer" class="btn btn-square btn-ghost">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						class="inline-block w-6 h-6 stroke-current"
						><path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/></svg
					>
				</label>
			</div>
			<div class="flex-1 px-2 mx-2">Insert Icon Here</div>
			<div class="flex-none hidden lg:block">
				<ul class="menu menu-horizontal">
					<!-- Navbar menu content here -->
					<li><a>Home</a></li>
					<li><a>About</a></li>
					<li><a>Gallery</a></li>
					<li><a>Committee</a></li>
				</ul>
			</div>
		</div>
		<slot /> 
	</div>
	<div class="drawer-side">
		<label for="side-drawer" class="drawer-overlay" />
		<ul class="menu p-4 overflow-y-auto w-80 bg-base-100">
			<!-- Sidebar content here -->
			<li class="flex flex-row-reverse align-middle items-end"><label for="side-drawer" class="btn btn-ghost btn-xl flex-shrink"><iconify-icon class="text-4xl" icon="carbon:close" /></label></li>
			<li><a>Home</a></li>
			<li><a>About</a></li>
			<li><a>Gallery</a></li>
			<li><a>Committee</a></li>
		</ul>
	</div>
</div>

  <style>
	.backdrop {
	  position: fixed;
	  top: 0;
	  bottom: 0;
	  right: 0;
	  left: 0;
	  background: rgba(0,0,0,0.50)
	}
  </style>



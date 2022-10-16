<script lang="ts">
	import { page } from '$app/stores';
	import 'iconify-icon';
	import { onMount, type SvelteComponent } from 'svelte';
	import { events } from '$lib/data/events';
	import type { PageData } from './$types';
	import { openModal } from 'svelte-modals';
	import SelectEventModal from '$lib/components/SelectEventModal.svelte';
	export let data: PageData;

	function validate_and_submit_form() {}
</script>

<div
	class="container max-w-4xl flex flex-col items-stretch justify-center bg-base-200 mt-16 rounded-xl p-8"
>
	<div class="title text-center">
		<span class="text-4xl vimh">Registration Form</span>
	</div>
	<div
		class="event-details flex flex-col-reverse md:flex-row items-center justify-between border-b border-base-content mx-8 p-4"
	>
		<div class="text-content flex flex-col">
			<div class="data-pair text-sm">
				<span class="text-lg text-bold mr-2">Event Name: </span>{data.name}
			</div>
			<div class="data-pair text-sm">
				<span class="text-lg text-bold mr-2">Event Details:</span>{data.desc}
			</div>
			<div class="data-pair text-sm">
				<span class="text-lg text-bold mr-2">Event Fees:</span><iconify-icon
					icon="carbon:currency-rupee"
				/>{data.amount / 100}
			</div>
			<div class="text-sm mt-4">
				<button
					on:click={() => {
						openModal(SelectEventModal);
					}}
					class="link py-2 pr-2">Select a different event</button
				>
			</div>
		</div>
		<div class="event-icon">
			<iconify-icon icon={data.icon} class="text-6xl text-primary" />
		</div>
	</div>
	<div class="form-container form-control items-center justify-evenly">
		<div class="input-field">
			<label for="name" class="label">
				<span class="label-text">Name</span>
			</label>
			<label class="input-group">
				<span><iconify-icon height="1.5rem" width="1.5rem" icon="ant-design:user-outlined" /></span>
				<input id="name" type="text" placeholder="John Doe" class="input input-bordered" />
			</label>
		</div>
		<div class="input-field">
			<label for="email" class="label">
				<span class="label-text">Email</span>
			</label>
			<label class="input-group">
				<span><iconify-icon height="1.5rem" width="1.5rem" icon="mdi:email" /></span>
				<input id="email" type="text" placeholder="email@site.com" class="input input-bordered" />
			</label>
		</div>
		<div class="input-field">
			<label for="mobile" class="label">
				<span class="label-text">Phone Number</span>
			</label>
			<label class="input-group">
				<span><iconify-icon height="1.5rem" width="1.5rem" icon="mdi:phone" /></span>
				<input id="mobile" type="text" placeholder="1234567890" class="input input-bordered" />
			</label>
		</div>
		<div class="input-field">
			<label for="education" class="label">
				<span class="label-text">College/School</span>
			</label>
			<label class="input-group">
				<span><iconify-icon height="1.5rem" width="1.5rem" icon="mdi:school" /></span>
				<input id="education" type="text" placeholder="GCOEN" class="input input-bordered" />
			</label>
		</div>
		<div class="input-field">
			<label for="email" class="label">
				<span class="label-text">Grade/Year</span>
			</label>
			<label class="input-group">
				<span><iconify-icon height="1.5rem" width="1.5rem" icon="mdi:label-variant-outline" /></span
				>
				<input id="email" type="text" placeholder="First Year" class="input input-bordered" />
			</label>
		</div>
		{#each Array(data.players - 1) as player, i}
			<div class="input-field">
				<label for="team-{i}" class="label">
					<span class="label-text">Team Member {i + 1}'s name</span>
				</label>
				<label class="input-group">
					<span
						><iconify-icon
							height="1.5rem"
							width="1.5rem"
							icon="ant-design:user-add-outlined"
						/></span
					>
					<input id="team-{i}" type="text" placeholder="Jane Doe" class="input input-bordered" />
				</label>
			</div>
		{/each}
	</div>
</div>

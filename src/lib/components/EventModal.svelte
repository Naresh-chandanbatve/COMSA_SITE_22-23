<script lang="ts">
	import { closeModal } from 'svelte-modals';

	// provided by <Modals />
	export let isOpen: boolean;
</script>

{#if isOpen}
	<div class="s-modal z-[200]">
		<div class="modal-container">
			<img class="image" src="http://placeimg.com/400/400/tech" alt="Event Description" />
			<div class="text-container">
				<h1 class="title vimh">Heading</h1>
				<div class="date">Date: Yes</div>
				<div class="description">
					<p>
						Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tenetur iure harum quam sequi
						dolor sapiente corrupti, quos praesentium exercitationem quibusdam distinctio ducimus
						fugit expedita? Nostrum quia corrupti facere neque rerum!
					</p>
					<p>
						Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatem sint provident id
						doloribus minima non odio maxime beatae dignissimos quos voluptatibus doloremque
						perferendis qui asperiores, autem necessitatibus dolore officiis nobis.
					</p>
				</div>
				<div class="flex flex-col p-2 gap-4 w-full">
					<button class="btn btn-block btn-primary" id="btn-1">Register</button>
					<button class="btn btn-block btn-secondary" on:click={closeModal} id="btn-2">Back</button>
				</div>
			</div>
		</div>
	</div>
{/if}

<style lang="postcss">
	  .s-modal {
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
	
    /* allow click-through to backdrop */
    pointer-events: none;
  }
	.modal-container {
		/* background-color: blueviolet; */
		padding: 2rem;
		display: flex;
		flex-direction: column;
		overflow: scroll;
		@apply w-full h-full pointer-events-none min-w-[15rem] self-center;
	}

	.modal-container * {
		@apply pointer-events-auto;
	}

	.image {
		/* max-width: 70vw; */
		max-height: auto;
		border-radius: 1rem 1rem 0 0;
		@apply container;
	}

	.text-container {
		/* max-width: 70vw; */
		/* background-color: red; */
		padding: 0.5rem 1.5rem;
		border-radius: 0 0 1rem 1rem;
		@apply container bg-base-300;
	}


	.title {
		/* line-height: 3.75rem; */
		font-size: 3.5rem;
		/* margin-left: 1rem; */
		/* padding: 0.5rem; */
		/* @apply bg-base-100; */
	}

	.date {
		/* background-color: yellow; */
		margin: 0 0 1rem 0rem;
		line-height: 1.75rem;
		font-size: 1.5rem;
		/* @apply bg-base-100; */
	}

	.description {
		/* background-color: aqua; */
		padding: 1rem;
		margin-bottom: 1rem;
		font-size: 1.05rem;
		@apply bg-base-100 rounded-xl;
	}

	@media only screen and (min-width: 1025px) {
		.modal-container {
			flex-direction: row;
			/* max-width: 90vw; */
		}

		.image {
			/* max-width: 40vw; */
			max-height: auto;
			border-radius: 1rem 0 0 1rem;
		}

		.text-container {
			border-radius: 0 1rem 1rem 0;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
		}
	}
</style>

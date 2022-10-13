<script>
  import {openModal} from 'svelte-modals';
  import EventModal from '$lib/components/EventModal.svelte';
  // openModal(EventModal, { title: "Alert", message: "This is an alert" })
  let onLearnMore = () => {
    openModal(EventModal, { title: "Alert", message: "This is an alert" })
  }
</script>

<div class="card max-w-xs min-h-[25vh] lg:min-h-0 md:max-w-md lg:max-w-lg aspect-video bg-base-100 shadow-xl image-full max-h-60">
    <figure><img src="https://placeimg.com/400/225/arch" alt="Shoes" /></figure>
    <div class="card-body">
      <h2 class="card-title vimh">CodeChamp v6.9</h2>
      <p>If a dog chews shoes whose shoes does he choose?</p>
      <div class="card-actions justify-end">
        <button  class="btn btn-primary">Register</button>
        <button on:click={onLearnMore} class="btn">Learn More</button>
      </div>
    </div>
  </div>
<script lang="ts">
	import FaqItem from "./FAQItem.svelte";
    import {page_0, page_0_title} from "$lib/data/FAQs";
    export let data_list = page_0;
    export let title = page_0_title;
</script>


<div class="faq">
    <h5 class="text-4xl">{title}</h5>
    {#each data_list as data}
        <FaqItem {...data}/>
    {/each}
</div>

<style lang="postcss">

h5 {
    text-align: center;
    margin: 1rem 0;
}

.faq {
    /* background: linear-gradient(to top right, rgba(51, 51, 213, 0.712), rgba(203, 73, 73, 0.734)); */
    color: rgb(255, 255, 255);
    max-width: 100vw;
    font-family: cursive;
    margin: auto;
    border-radius: 5px;
    font-size: 1.25rem;
    padding: .5rem;
    @apply w-full h-full container flex flex-col justify-evenly items-center;
}

</style>
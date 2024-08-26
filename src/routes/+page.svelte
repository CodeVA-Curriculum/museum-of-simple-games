<script lang='ts'>
    import { onMount } from "svelte";

    let games = ['picman', 'galaxis', 'tanks', 'waddleball', 'starbase', 'breakout']

    let show = true
    let timer = 0
    const minutes = 10

    onMount(() => {
        setTimeout(() => {show = false}, 1000 * 60 * minutes)
        setInterval(() => { timer++ }, 1000)
    })


</script>

<div class='container mx-auto'>
    <section class='flex justify-center mb-3 mt-20'>
        <h1 class="mb-4 text-4xl font-extrabold md:text-5xl lg:text-6xl">The Museum of Simple Games</h1>
    </section>
    <section class='flex justify-center mb-9'>
        <p class='text-2xl'>{`${Math.floor(timer/60) < 10? '0':''}${Math.floor(timer/60)}:${timer%60<10? '0':''}${timer % 60}`}</p>
    </section>
    {#if show}
    <section class='grid grid-cols-2 gap-4 py-3'>
        {#each games as game}
        <div class='flex justify-center'>
            <iframe src="/museum-of-simple-games/games/{game}/{game}.html" allowfullscreen width="621" height="513" style="border:none; overflow:hidden"></iframe>    
        </div>
        {/each}
        <!-- <div class='flex justify-center'>
            <iframe src="/museum-of-simple-games/games/picman/picman.html" allowfullscreen width="621" height="513" style="border:none; overflow:hidden"></iframe>    
        </div> -->
    </section>
    {:else}
    <div class='flex justify-center my-9'>
        <p>Your time is up!</p>
    </div>
    {/if}
</div>

<style>
    /* section {
        background-color: pink;
    } */
</style>
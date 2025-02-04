<script>
    let { quote = "Quote", author = "Smart Kar", year = 2025, image = "https://placehold.co/500x600", alt = "image", direction = "left"} = $props();
</script>

<div class="splash">
    {#if direction === "left"}
         <div class="quote">
             <q>{quote}</q>
             <p> - {author}, {year} </p>
         </div>
         <img src="{image}" alt="{alt}" class="info">
    {:else}
        <img src="{image}" alt="{alt}" class="info">
        <div class="quote">
             <q>{quote}</q>
             <p> - {author}, {year} </p>
         </div>
    {/if}
</div>

<style>
    .splash {
        height: 100vh;
        width: 100vw;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }
    q {
        font-size: 128px;
        font-weight: 700;
    }

    p {
        font-size: 36px;
        font-weight: 400;
        margin-left: 150px;
    }
</style>
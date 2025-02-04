<script>
    let { header = "Header", 
    text = "pariatur ullamco cillum id et pariatur commodo ad mollit consectetur sunt adipisicing dolor ad ad do mollit minim elit quis labore pariatur id enim pariatur", 
    image = "https://placehold.co/500x600", 
    alt = "image", 
    direction = "right"} = $props();
</script>

<div class="textBox">
    {#if direction === "left"}
        <div class="text">
            <h1>{header}</h1>
            <p>{text}</p>
        </div>
        <img src="{image}" alt="{alt}">
    {:else}
        <img src="{image}" alt="{alt}">
        <div class="text">
            <h1>{header}</h1>
            <p>{text}</p>
        </div>
    {/if}
</div>

<style>
    .textBox {
        background-color: #383838;
        height: 100vh;
        width: 100vw;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }

    .text {
        width: 40vw;
    }

    h1 {
        font-size: 96px;
        font-weight: 700;
    }

    p {
        font-size: 28px;
        font-weight: 300;
    }
</style>
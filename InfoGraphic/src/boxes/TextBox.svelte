<script>
    let { header = "Header", 
    text = "pariatur ullamco cillum id et pariatur commodo ad mollit consectetur sunt adipisicing dolor ad ad do mollit minim elit quis labore pariatur id enim pariatur", 
    image = "https://placehold.co/500x600", 
    alt = "image", 
    direction = "right"} = $props();
</script>

<div class="textBox">
    {#if direction === "left"}
        <div class="text" data-aos="fade-right" data-aos-duration="500">
            <h1>{header}</h1>
            <p>{text}</p>
        </div>
        <img src="{image}" alt="{alt}" data-aos="zoom-in" data-aos-duration="500">
    {:else}
        <img src="{image}" alt="{alt}" data-aos="zoom-in" data-aos-duration="500">
        <div class="text" data-aos="fade-left" data-aos-duration="500">
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
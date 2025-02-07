<script>
    import { onMount } from 'svelte';
    import Navbar from "../components/navbar.svelte";
    import AOS from 'aos';
    import 'aos/dist/aos.css';

    let loading = true;

    onMount(() => {
        setTimeout(() => {
            loading = false;
            AOS.init();
        }, 1500); // Varighet av loading-animasjonen i millisekunder
    });
</script>

<Navbar />
<slot></slot>

<div class="loader" class:hide={!loading}>
    <div class="loader-text">Rus Er Ikke Bra</div>
</div>

<style>
    .loader {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #111111;
        z-index: 10000;
        transition: opacity 0.5s ease;
    }

    .loader.hide {
        opacity: 0;
        pointer-events: none;
    }

    .loader-text {
        font-size: 48px;
        font-weight: bold;
        color: #BB86FC;
        animation: pulse 1.5s;
    }

    @keyframes pulse {
        0% {
            transform: scale(1);
            opacity: 1;
        }
        50% {
            transform: scale(1.1);
            opacity: 0.7;
        }
        100% {
            transform: scale(1);
            opacity: 1;
        }
    }
</style>
<script lang="ts">
    import { onMount } from 'svelte';

    // Initialiserer variabler for å spore siste scroll-posisjon og synligheten til navbar
    let lastScrollTop = 0;
    let navbarVisible = $state(true);

    // Funksjon for å sjekke brukerens scroll-retning
    const checkScroll = () => {
        // Henter nåværende scroll-posisjon
        let st = window.pageYOffset || document.documentElement.scrollTop;
        // Skjuler navbar hvis brukeren scroller nedover, viser den hvis oppover
        if (st > lastScrollTop){
            navbarVisible = false;
        } else {
            navbarVisible = true;
        }
        // Oppdaterer siste kjente scroll-posisjon, resetter til 0 hvis negativ
        lastScrollTop = st <= 0 ? 0 : st;
    };

    onMount(() => {
        // Legger til scroll-event listener hvis window-objektet er tilgjengelig
        if (typeof window !== 'undefined') {
            window.addEventListener('scroll', checkScroll);
        }

        // Fjerner event listener når komponenten demonteres
        return () => {
            if (typeof window !== 'undefined') {
                window.removeEventListener('scroll', checkScroll);
            }
        };
    });

    const links = [
        {name: 'Hjem', href: '/'},
        {name: 'Lorem', href: '/lorem'},
        {name: 'Kilder', href: '/kilder'},
    ];

</script>

<div class="navbar" class:hide={!navbarVisible}>
    <a href="/">
        <div class="logo-container">
            <img src="/images/logo-hvit.png" alt="Home" class="logo" id="logo">
        </div>
    </a>
    <div class="nav-links thin">
        {#each links as link}
            <a href={link.href} class="effect-underline">
                {link.name}
            </a>
        {/each}
    </div>
</div>

<nav class="menu--right">
    <div class="menuToggle">
        <input type="checkbox"/>
        <span></span>
        <span></span>
        <span></span>
        <ul class="menuItem">
            <li><a href="/" class="effect-underline">Home</a></li>
            {#each links as link}
                <li>
                    <a href={link.href} class="effect-underline">
                        {link.name}
                    </a>
                </li>
            {/each}
        </ul>
    </div>
</nav>

<style>
    /* Variables */
    :root {
        --nav-heigt: 80px;
        --text-size: 20px;
    }

    #logo {
        height: 70%;
        transition: all 0.3s ease;
    }

    #logo:hover {
        cursor: pointer;
        content: url('/images/logo-lilla.png');
        scale: 1.1;
    }

    .logo-container {
        display: flex;
        align-items: center;
        height: var(--nav-heigt);
    }
    .navbar {
        transition: top 0.3s;
        position: fixed;
        height: var(--nav-heigt);
        top: 0;
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 20px;
        font-size: var(--text-size);
        font-weight: 200;
        color: #E2E2E2;
        background-color: #111111;
        z-index: 10000;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .nav-links {
        display: flex;
        list-style: none;
        align-items: center;
        color: inherit;
    }

    .nav-links a {
        margin-right: 56px;
        text-decoration: none;
        color: inherit;
        text-align: center;
        transition: all 0.3s ease;
    }

    .nav-links a:hover {
        color: #BB86FC;
        scale: 1.1;
    }

    .navbar.hide {
        top: calc(-1 * var(--nav-heigt));
    }

    .menu--right {
        display: none;
    }

    @media screen and (max-width: 1050px) {
        .navbar {
            display: none;
        }

        .menu--right {
            display: block;
            z-index: 100000;
        }
        .menuToggle {
            display: block;
            position: relative;
            top: 50px;
            z-index: 1;
            -webkit-user-select: none;
            user-select: none;
        }
        .menuToggle a {
            text-decoration: none;
            color: #232323;
            transition: all 0.3s ease;
        }
        .menuToggle input {
            display: block;
            width: 40px;
            height: 32px;
            position: absolute;
            top: -7px;
            cursor: pointer;
            opacity: 0;
            /* hide this */
            z-index: 2;
            /* and place it over the hamburger */
            -webkit-touch-callout: none;
        }
        .menuToggle span {
            position: relative;
            display: block;
            width: 33px;
            height: 4px;
            margin-bottom: 5px;
            position: relative;
            background: #cdcdcd;
            border-radius: 3px;
            z-index: 1;
            transform-origin: 4px 0px;
            transition: transform 0.5s cubic-bezier(0.77, 0.2, 0.05, 1), background 0.5s cubic-bezier(0.77, 0.2, 0.05, 1), opacity 0.55s ease;
        }
        .menuToggle span:first-child {
            transform-origin: 0% 0%;
        }
        .menuToggle span:nth-last-child(2) {
            transform-origin: 0% 100%;
        }
        .menuToggle input:checked ~ span {
            opacity: 1;
            transform: rotate(45deg) translate(-2px, -1px);
            background: #232323;
        }
        .menuToggle input:checked ~ span:nth-last-child(3) {
            opacity: 0;
            transform: rotate(0deg) scale(0.2, 0.2);
        }
        .menuToggle input:checked ~ span:nth-last-child(2) {
            transform: rotate(-45deg) translate(0, -1px);
        }
        .menuToggle input:checked ~ .menuItem {
            transform: none;
        }
        .menuItem {
            position: absolute;
            width: 300px;
            padding: 50px;
            padding-top: 125px;
            background: #ededed;
            list-style-type: none;
            transform-origin: 0% 0%;
            transition: transform 0.5s cubic-bezier(0.77, 0.2, 0.05, 1);
        }
        .menuItem li {
            padding: 10px 0;
            font-size: 22px;
        }
        .menu--right .menuToggle {
            position: fixed;
            right: 0;
        }
        .menu--right .menuToggle input {
            right: 50px;
        }
        .menu--right .menuToggle span {
            right: 50px;
        }
        .menu--right .menuItem {
            right: 0;
            margin: -100px 0 0 0;
            transform: translate(100%, 0);
        }
    }
</style>
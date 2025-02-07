<script>
    let kilder =[
        {
            "tittel": "Røyk, alkohol og andre rusmidler",
            "årstall": "Ukjent",
            "link": "https://www.ssb.no/helse/helseforhold-og-levevaner/statistikk/royk-alkohol-og-andre-rusmidler"
        },
        {
            "tittel": "Rusmiddelbruk i Norge 2010",
            "årstall": 2010,
            "link": "https://www.fhi.no/globalassets/dokumenterfiler/rapporter/2010/sirusrap.4.10.pdf"
        },
        {
            "tittel": "Ungdom og rus",
            "årstall": "Ukjent",
            "link": "https://www.blakors.no/fagside/ungdom-og-rus/"
        },
        {
            "tittel": "Folk flest vet overraskende lite om rusmidler",
            "årstall": "Ukjent",
            "link": "https://rusinfo.no/aktuelt/folk-flest-vet-overraskende-lite-om-rusmidler/"
        },
        {
            "tittel": "Narkotikabruk i Norge",
            "årstall": "Ukjent",
            "link": "https://www.fhi.no/le/rusmidler-og-avhengighet/narkotikainorge/bruk-av-narkotika/narkotikabruk-i-norge/?term="
        },
        {
            "tittel": "Hemmeligheter om rus og avhengighet",
            "årstall": "Ukjent",
            "link": "https://www.blakors.no/fagside/hemmeligheter-om-rus-og-avhengighet/"
        },
        {
            "tittel": "Rusmiddelbruk blant sysselsatte i Norge 2013-2022",
            "årstall": 2024,
            "link": "https://www.fhi.no/globalassets/dokumenterfiler/rapporter/2024/rusmiddelbruk-blant-sysselsatte-i-norge-2013-2022_fhi-rapport-januar-2024.pdf"
        },
        {
            "tittel": "Fakta om rusmidler",
            "årstall": "Ukjent",
            "link": "https://www.oslo-universitetssykehus.no/fag-og-forskning/nasjonale-og-regionale-tjenester/tsb/fakta-om-rusmidler/"
        }];
</script>

<h1 data-aos="fade-down">Kilder</h1>

{#each kilder as kilde, index}
    <div class="kilde {index % 2 === 0 ? 'grey' : ''}" data-aos="fade-up" data-aos-delay={100}>
        <h2>{kilde.tittel}, {kilde.årstall}</h2>
        <a href="{kilde.link}">{kilde.link}</a>
    </div>
{/each}


<style>
    h1 {
        width: 100%;
        margin: 0 auto;
        margin-top: 200px;
        font-size: 200px;
        text-align: center;
    }

    .kilde {
        width: 100%;
        height: 128px;
        display: flex;
        justify-content: center;
        flex-direction: column;
        gap: 10px;
        padding-left: 50px;
    }

    .kilde.grey {
        background-color: #383838;
    }

    a {
        transition: all .3s;
    }

    a:hover {
        color: #BB86FC;
    }
</style>
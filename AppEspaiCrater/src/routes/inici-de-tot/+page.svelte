<script>
    import Line from "../../components/svg/line.svelte";
</script>

<main class="flex flex-col py-15 px-20 gap-4 theme-terra">
    <Line svgClass="text-theme w-full h-3" squareWidth={2} />
    <div class="grid grid-cols-3 gap-x-10">
        <div class="flex flex-col gap-6">
            <h1
                class="text-theme text-[5.5vw] leading-none font-semibold uppercase"
            >
                QUÈ ÉS EL MAGMA?
            </h1>
            <img
                src="https://i0.wp.com/enfermeriacreativa.com/wp-content/uploads/2019/07/placeholder.png?ssl=1"
                alt=""
                class="rounded-br-2xl rounded-tl-2xl"
            />
        </div>
        <div class="flex flex-col">
            <p class="text-title font-semibold">
                Els magmes són barreges de material rocós fos, que poden
                contenir particules sòlides, minerals i fragments de roques i
                gasos dissolts
            </p>
            <a
                href="/inici-de-tot/subpagina"
                class="button font-bold uppercase"
            >
                Formació
            </a>
            <a href="/inici-de-tot/subpagina" class="button uppercase">
                Composició
            </a>
        </div>
        <div class="flex flex-col">
            <a href="/inici-de-tot/subpagina" class="button">Ascens</a>
            <a
                href="/inici-de-tot/subpagina"
                class="button font-bold uppercase"
            >
                Erupció
            </a>
        </div>
    </div>
</main>

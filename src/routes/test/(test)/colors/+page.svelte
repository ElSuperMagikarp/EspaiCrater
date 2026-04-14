<main class="grid grid-cols-2 auto-rows-fr">
    <div class="colorsColumn">
        <div class="color bg-crater">Espai Crater</div>
        <div class="color bg-greda">La Greda</div>
        <div class="flex-1 grid grid-cols-2">
            <div class="color bg-terra-1">La Terra 1</div>
            <div class="color bg-terra-2">La Terra 2</div>
        </div>
        <div class="color bg-garrotxa-1">La Garrotxa 1</div>
        <div class="color bg-garrotxa-2">La Garrotxa 2</div>
    </div>
    <div class="colorsColumn">
        <div class="color bg-volcanic-1">Volcanic 1</div>
        <div class="color bg-volcanic-2">Volcanic 2</div>
        <div class="color bg-volcanic-3">Volcanic 3</div>
        <div class="color bg-volcanic-4">Volcanic 4</div>
        <div class="color bg-volcanic-5">Volcanic 5</div>
    </div>
</main>

<style>
    @reference "tailwindcss";

    .colorsColumn {
        @apply flex-1 flex flex-col;
    }

    .color {
        @apply flex-1 flex justify-center items-center text-white;
    }
</style>

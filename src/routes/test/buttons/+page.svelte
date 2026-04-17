<script>
    const themes = [
        "theme-crater",
        "theme-terra",
        "theme-garrotxa",
        "theme-volcanic",
    ];
</script>

<main class="flex flex-col bg-gray-900">
    {#each themes as theme}
        <div
            class="flex-1 {theme} flex-center py-4
                border-x-(--theme-color) border-x-8
                border-y-gray-800 border-y-2"
        >
            <div class="flex flex-col gap-y-2">
                <h1 class="text-xl text-(--theme-color)">{theme}</h1>
                <div class="menu flex gap-4">
                    <button class="button">Unactive Button</button>
                    <button class="button active">Active Button</button>
                    <div class="submenu flex gap-4">
                        <button class="button">Unactive Button</button>
                        <button class="button active">Active Button</button>
                    </div>
                </div>
            </div>
        </div>
    {/each}
</main>

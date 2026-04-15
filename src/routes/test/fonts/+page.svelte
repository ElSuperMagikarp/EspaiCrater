<script>
    const fonts = [
        "font-light",
        "font-normal",
        "font-medium",
        "font-semibold",
        "font-semibold italic",
        "font-bold",
        "font-black",
        "font-space-mono",
    ];
</script>

<main class="flex-center py-4 bg-white">
    <div class="flex flex-col gap-10">
        {#each fonts as font}
            <div class="flex flex-col">
                <h2 class="text-crater"><strong>Font:</strong> {font}</h2>
                <p class="text-black text-2xl {font}">
                    abcdefghijklmnñopqrstuvxyz <br />
                    ABCDEFGHIJKLMNÑOPQRSTUVWXYZ <br />
                    1234567890,.?¿´-
                </p>
            </div>
        {/each}
    </div>
</main>

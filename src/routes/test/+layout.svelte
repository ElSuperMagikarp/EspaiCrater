<div class="absolute top-2 left-1">
    <button
        class="p-1 bg-white hover:bg-gray-400 rounded-md hover:cursor-pointer"
        on:click={() => history.back()}
    >
        &lt; Go back
    </button>
</div>

<slot />

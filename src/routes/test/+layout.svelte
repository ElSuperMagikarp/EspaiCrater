<div class="fixed top-2 left-1">
    <button
        class="p-1 px-2 bg-white border border-crater hover:bg-gray-300 rounded-md hover:cursor-pointer"
        on:click={() => history.back()}
    >
        &lt; Go back
    </button>
</div>

<slot />

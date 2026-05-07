<script lang="ts">
    import { onMount } from "svelte";

    type Theme =
        | "theme-crater"
        | "theme-terra"
        | "theme-garrotxa"
        | "theme-volcanic";

    let { screenName, theme } = $props<{
        screenName: string;
        theme: Theme;
    }>();

    const State = {
        Idle: "idle",
        Intro: "intro",
        Hidden: "hidden",
    };

    let state = $state(State.Idle);

    function handleClick() {
        if (state === State.Idle) {
            state = State.Intro;
        } else if (state === State.Intro) {
            state = State.Hidden;
        }
    }

    // INACTIVITY
    const INACTIVITY_MS = 3 * 60 * 1000;

    let inactivityTimeout: ReturnType<typeof setTimeout>;

    function resetInactivityTimer() {
        clearTimeout(inactivityTimeout);

        inactivityTimeout = setTimeout(() => {
            state = State.Idle;
        }, INACTIVITY_MS);
    }

    function handleActivity() {
        resetInactivityTimer();
    }

    onMount(() => {
        resetInactivityTimer();

        window.addEventListener("click", handleActivity);

        return () => {
            clearTimeout(inactivityTimeout);

            window.removeEventListener("click", handleActivity);
        };
    });
</script>

{#if state !== State.Hidden}
    <button
        class="w-full h-screen flex-center
            bg-black
            absolute text-white
            {theme}"
        onclick={handleClick}
    >
        {#if state === State.Idle}
            <h1 class="text-2xl font-bold select-none uppercase">
                {screenName}
            </h1>
        {:else if state === State.Intro}
            <h1 class="text-2xl font-bold select-none uppercase">Intro</h1>
        {/if}
    </button>
{/if}

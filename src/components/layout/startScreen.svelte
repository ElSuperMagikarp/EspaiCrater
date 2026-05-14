<script lang="ts">
    import { onMount } from "svelte";
    import { page } from "$app/state";
    import { goto } from "$app/navigation";

    type Theme =
        | "theme-crater"
        | "theme-terra"
        | "theme-garrotxa"
        | "theme-volcanic";

    let { screenName, welcomeMessage, theme, initialRoute } = $props<{
        screenName: string;
        welcomeMessage: string;
        theme: Theme;
        initialRoute: string | null;
    }>();

    const State = {
        Idle: "idle",
        Intro: "intro",
        Hidden: "hidden",
    };

    let screenState = $state(State.Idle);

    function handleClick() {
        if (screenState === State.Idle) {
            screenState = State.Intro;
        } else if (screenState === State.Intro) {
            goto(initialRoute);
            screenState = State.Hidden;
        }
    }

    // INACTIVITY
    const INACTIVITY_MS = 3 * 60 * 1000;

    let inactivityTimeout: ReturnType<typeof setTimeout>;

    function resetInactivityTimer() {
        clearTimeout(inactivityTimeout);

        inactivityTimeout = setTimeout(() => {
            screenState = State.Idle;
            goto(initialRoute);
        }, INACTIVITY_MS);
    }

    function handleActivity() {
        resetInactivityTimer();
    }

    onMount(() => {
        goto(initialRoute);
        resetInactivityTimer();

        window.addEventListener("click", handleActivity);

        return () => {
            clearTimeout(inactivityTimeout);

            window.removeEventListener("click", handleActivity);
        };
    });
</script>

{#if screenState !== State.Hidden}
    <button
        class="w-full h-screen flex-center
            bg-black
            absolute text-white
            {theme}"
        onclick={handleClick}
    >
        {#if screenState === State.Idle}
            <h1 class="text-2xl font-bold select-none uppercase">
                {screenName}
            </h1>
        {:else if screenState === State.Intro}
            <div class="flex flex-col gap-y-3">
                <h1 class="text-2xl font-bold select-none uppercase">HOLA!</h1>
                <p>{welcomeMessage}</p>
            </div>
        {/if}
    </button>
{/if}

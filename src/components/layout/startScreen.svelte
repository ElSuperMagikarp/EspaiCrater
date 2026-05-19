<script lang="ts">
    import { onMount } from "svelte";
    import { goto } from "$app/navigation";
    import type { ScreenTheme } from "$lib/types/screenTheme";
    import AnimatedBackground from "./animatedBackground.svelte";
    import Arrow from "../svg/arrow.svelte";

    let { screenName, welcomeMessage, theme, initialRoute } = $props<{
        screenName: string;
        welcomeMessage: string;
        theme: ScreenTheme;
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
    <div class="absolute size-full">
        <AnimatedBackground {theme} />

        <button
            class="w-full h-screen flex-center
                overflow-hidden
                absolute text-white
                {theme}"
            onclick={handleClick}
        >
            <div class="relative z-10">
                {#if screenState === State.Idle}
                    <h1 class="text-7xl font-bold select-none uppercase">
                        {screenName}
                    </h1>
                {:else if screenState === State.Intro}
                    <div class="flex-center flex-col gap-y-4">
                        <h1 class="text-6xl font-bold select-none uppercase">
                            HOLA!
                        </h1>

                        <p class="text-4xl select-none">{welcomeMessage}</p>

                        <Arrow size={8} strokeWidth={0.2} direction="down" />
                    </div>
                {/if}
            </div>
        </button>
    </div>
{/if}

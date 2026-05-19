<script lang="ts">
    import type { ScreenTheme } from "$lib/types/screenTheme";

    let {
        theme,
        darkened = false,
    }: {
        theme: ScreenTheme;
        darkened?: boolean;
    } = $props();

    const videoSources: Record<ScreenTheme, string> = {
        "theme-crater": "src/lib/videos/background_volcanic.mp4",
        "theme-terra": "src/lib/videos/background_terra.mp4",
        "theme-garrotxa": "src/lib/videos/background_garrotxa.mp4",
        "theme-volcanic": "src/lib/videos/background_volcanic.mp4",
    };

    const src = videoSources[theme];
</script>

<video
    autoplay
    muted
    loop
    playsinline
    class="absolute inset-0 size-full object-cover"
>
    <source {src} type="video/mp4" />
</video>

{#if darkened}
    <div class="absolute inset-0 bg-black/40"></div>
{/if}

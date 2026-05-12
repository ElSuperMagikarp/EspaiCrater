<script lang="ts">
    import Corner from "./parts/cornerBlock.svelte";
    import SideSymbol from "../primitives/sideSymbol.svelte";
    import Logo from "../primitives/logo.svelte";

    import StartScreen from "./startScreen.svelte";

    type Theme =
        | "theme-crater"
        | "theme-terra"
        | "theme-garrotxa"
        | "theme-volcanic";

    let { overlayText, screenName, welcomeMessage, theme } = $props<{
        overlayText: string;
        screenName: string;
        welcomeMessage: string;
        theme: Theme;
    }>();

    let generalClasses = "absolute";

    let top = "top-3";
    let bottom = "bottom-3";
    let left = "left-4 flex-row";
    let right = "right-4 flex-row-reverse";
    let ycenter = "top-1/2 -translate-y-1/2";
    let xcenter = "left-1/2 -translate-x-1/2";

    let cornersStrokeWidth = 2;
    let cornerSize = 17;
    let sideSymbolsStrokeWidth = 0.3;
    let sideSymbolSize = 32;
    let logoSize = 32;

    // DATE/TIME
    import { onMount } from "svelte";

    let now = new Date();

    let time = $state("");
    let date = $state("");

    function updateFormatted() {
        const h = String(now.getHours()).padStart(2, "0");
        const m = String(now.getMinutes()).padStart(2, "0");
        const s = String(now.getSeconds()).padStart(2, "0");

        time = `${h}:${m}:${s}`;

        const y = now.getFullYear();
        const mo = now.getMonth() + 1; // months are 0-based
        const d = now.getDate();

        date = `${y}.${mo}.${d}`;
    }

    onMount(() => {
        const interval = setInterval(() => {
            now = new Date();
            updateFormatted();
        }, 1000);

        updateFormatted(); // initial call

        return () => clearInterval(interval);
    });
</script>

<!-- START SCREEN -->
<StartScreen {screenName} {welcomeMessage} {theme} />

<!-- OVERLAY -->
<div
    class="w-full h-screen
            absolute pointer-events-none
            text-white text-xs
            {theme}"
>
    <!-- Top/Left -->
    <div class="{generalClasses} {top} {left}">
        <Corner corner="tl" strokeWidth={cornersStrokeWidth} size={cornerSize}>
            <p class="uppercase font-bold">{overlayText}</p>
        </Corner>
    </div>

    <!-- Top/Right -->
    <div class="{generalClasses} {top} {right}">
        <Corner corner="tr" strokeWidth={cornersStrokeWidth} size={cornerSize}>
            <div class="flex gap-2 pointer-events-auto">
                <button class="button bg-black/50">CAT</button>
                <button class="button bg-black/50">ES</button>
                <button class="button bg-black/50">ENG</button>
                <button class="button bg-black/50">FRA</button>
            </div>
        </Corner>
    </div>

    <!-- Bottom/Left -->
    <div class="{generalClasses} {bottom} {left}">
        <Corner corner="bl" strokeWidth={cornersStrokeWidth} size={cornerSize}>
            <span class="font-space-mono">E2°9'24.43" N42°10'51.46"</span>
        </Corner>
    </div>

    <!-- Bottom/Right -->
    <div class="{generalClasses} {bottom} {right}">
        <Corner corner="br" strokeWidth={cornersStrokeWidth} size={cornerSize}>
            <Logo size={logoSize} />
        </Corner>
    </div>

    <!-- Center/Left -->
    <div class="{generalClasses} {ycenter} {left}">
        <SideSymbol
            strokeWidth={sideSymbolsStrokeWidth}
            size={sideSymbolSize}
        />
    </div>

    <!-- Bottom/Center -->
    <div class="{generalClasses} {bottom} {xcenter} flex-center gap-4">
        <span class="font-space-mono">{time}</span>
        <span class="font-space-mono">{date}</span>
    </div>

    <!-- Center/Right -->
    <div class="{generalClasses} {ycenter} {right}">
        <SideSymbol
            strokeWidth={sideSymbolsStrokeWidth}
            size={sideSymbolSize}
        />
    </div>
</div>

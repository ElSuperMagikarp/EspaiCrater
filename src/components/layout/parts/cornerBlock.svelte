<script lang="ts">
    import Corner from "../../primitives/corner.svelte";
    import type { Snippet } from "svelte";

    type CornerType = "tl" | "tr" | "bl" | "br";

    let {
        corner = "tl",
        size = 16,
        strokeWidth = 1,
        children,
    }: {
        corner?: CornerType;
        size?: number;
        strokeWidth?: number;
        children?: Snippet;
    } = $props();

    const offsets: Record<CornerType, string> = {
        tl: "top-2 left-4",
        tr: "top-2 right-4",
        bl: "bottom-2 left-4",
        br: "bottom-2 right-4",
    };
</script>

<div class="relative">
    <Corner {corner} {size} {strokeWidth} />

    <div class={"absolute whitespace-nowrap " + offsets[corner]}>
        {@render children?.()}
    </div>
</div>

<script lang="ts">
    let {
        corner = "tl",
        size = 16,
        strokeWidth = 1,
    }: {
        corner?: "tl" | "tr" | "br" | "bl";
        size?: number;
        strokeWidth?: number;
    } = $props();

    const rotations = {
        tl: "rotate-0",
        tr: "rotate-90",
        br: "rotate-180",
        bl: "-rotate-90",
    };
</script>

<svg viewBox="0 0 10 10" class={rotations[corner]} width={size} height={size}>
    <path
        d="M0 10 L0 0 L10 0"
        fill="none"
        stroke="currentColor"
        stroke-width={strokeWidth}
    />
</svg>

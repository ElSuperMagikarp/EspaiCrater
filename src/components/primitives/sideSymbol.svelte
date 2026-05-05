<script>
    let { strokeWidth = 1, size = 16 } = $props();
</script>

<svg viewBox="0 0 20 20" width={size} height={size}>
    <circle
        cx="10"
        cy="10"
        r="5"
        fill="none"
        stroke="currentColor"
        stroke-width={strokeWidth}
    />
    <line
        x1="10"
        y1="0"
        x2="10"
        y2="20"
        stroke="currentColor"
        stroke-width={strokeWidth}
    />
    <line
        x1="0"
        y1="10"
        x2="20"
        y2="10"
        stroke="currentColor"
        stroke-width={strokeWidth}
    />
</svg>

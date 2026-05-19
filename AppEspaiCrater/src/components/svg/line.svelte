<script>
    let {
        svgClass = "",
        lineHeight = 1,
        squareHeight = 4,
        squareWidth = 10,
    } = $props();
</script>

<svg viewBox="0 0 100 10" preserveAspectRatio="none" class={svgClass}>
    <!-- Thick section -->
    <rect
        x="0"
        y="0"
        width={squareWidth}
        height={squareHeight}
        fill="currentColor"
    />

    <!-- Thin section -->
    <rect
        x={squareWidth}
        y="0"
        width={100 - squareWidth}
        height={lineHeight}
        fill="currentColor"
    />
</svg>

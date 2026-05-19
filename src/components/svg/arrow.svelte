<script lang="ts">
    let {
        direction = "right",
        customClasses = "",
        size = 5,
        strokeWidth = 1,
        animated = true,
    }: {
        direction?: "right" | "down" | "left" | "up";
        customClasses?: string;
        size?: number;
        strokeWidth?: number;
        animated?: boolean;
    } = $props();

    const rotations = {
        right: "rotate-0",
        down: "rotate-90",
        left: "rotate-180",
        up: "-rotate-90",
    };

    const marginValue = `${size * 0.25}rem`;

    const marginStyle = !animated
        ? ""
        : direction === "right"
          ? `margin-right: ${marginValue};`
          : direction === "left"
            ? `margin-left: ${marginValue};`
            : direction === "up"
              ? `margin-top: ${marginValue};`
              : `margin-bottom: ${marginValue};`;
</script>

<svg
    viewBox="0 0 20 15"
    class="{rotations[direction]} {customClasses}"
    style="
        width: {size}rem;
        height: {size}rem;
        {marginStyle}
        {animated ? 'animation: float-x 1.5s ease-in-out infinite;' : ''}
    "
>
    <path
        d="M0.5 7.5 L19.5 7.5Z M12.5 0.5 L19.5 7.5 L12.5 14.5"
        fill="none"
        stroke="currentColor"
        stroke-width={strokeWidth}
        stroke-linecap="round"
        stroke-linejoin="round"
    />
</svg>

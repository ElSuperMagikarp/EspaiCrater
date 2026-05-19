<script>
    import GlobalOverlay from "../../components/layout/globalOverlay.svelte";
    import { page } from "$app/state";

    const layoutBase = page.route.id;
</script>

<GlobalOverlay
    overlayText="Com Som"
    screenName="L'Inici de Tot"
    welcomeMessage="Endinsa’t al magma"
    theme="theme-terra"
    initialRoute={layoutBase}
>
    <slot />
</GlobalOverlay>

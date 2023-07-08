<script lang="ts">
    import FooterComp from "$lib/components/FooterComp.svelte";
    import HeaderComp from "$lib/components/HeaderComp.svelte";
    import { screenSizeStore } from "$lib/snipgen.store";
    import { onMount } from "svelte";
    import "../app.css";

    onMount(() => {
        $screenSizeStore = window.innerWidth;
        console.log("screenWidth", $screenSizeStore);
    });
</script>

<div data-theme="black" class="  h-screen">
    <HeaderComp />
    <slot />
    <FooterComp /> 
</div>

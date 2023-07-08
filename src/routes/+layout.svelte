<script lang="ts">
    import FooterComp from "$lib/components/FooterComp.svelte";
    import HeaderComp from "$lib/components/HeaderComp.svelte";
    import { screenSizeStore } from "$lib/snipgen.store";
    import { onMount } from "svelte";
    import "../app.css";
    import { dev } from '$app/environment';
    import { inject } from '@vercel/analytics';
    
    inject({ mode: dev ? 'development' : 'production' });

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

<script lang="ts">
    import { onMount } from "svelte";
    import FooterComp from "$lib/components/FooterComp.svelte";
    import SnippetEditorComp from "$lib/components/SnippetEditorComp.svelte";
    import HeaderComp from "../lib/components/HeaderComp.svelte";
    import SmallScreenComp from "$lib/components/SmallScreenComp.svelte";
    import LoaderComp from "$lib/components/LoaderComp.svelte";

    let screenWidth : number = 0;
    let loading: boolean = true;

    onMount(() => {
        screenWidth = window.innerWidth;
        console.log("screenWidth", screenWidth);
        loading = false;
    });
</script>

<div class="">
    {#if loading}
        <LoaderComp />
    {:else}
        <HeaderComp />
        {#if screenWidth < 800}
            <SmallScreenComp />
        {:else}
            <SnippetEditorComp />
        {/if}
        <FooterComp />
    {/if}
</div>

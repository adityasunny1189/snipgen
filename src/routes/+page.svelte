<script lang="ts">
    import { onMount } from "svelte";
    import SnippetEditorComp from "$lib/components/SnippetEditorComp.svelte";
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

<div class=" h-4/5">
    {#if loading}
        <LoaderComp />
    {:else}
        {#if screenWidth < 800}
            <SmallScreenComp />
        {:else}
            <SnippetEditorComp />
        {/if}
    {/if}
</div>

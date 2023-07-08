<script lang="ts">
    import SublimeComp from "./SublimeComp.svelte";
    import VscodeComp from "./VscodeComp.svelte";

    let vscodeTabActive: boolean = true;
    let sublimeTabActive: boolean = false;

    const handleTabSwitch = (editor : string) => {
        console.log("Tab Switched to ", editor);
        if (editor === "vscode") {
            vscodeTabActive = true;
            sublimeTabActive = false;
        } else {
            vscodeTabActive = false;
            sublimeTabActive = true;
        }
    }

</script>

<div class=" container mx-auto ">
    <!-- Tabs component -->
    <div class="tabs tabs-boxed">
        <button on:click={() => handleTabSwitch("vscode")} class="tab w-1/2 {vscodeTabActive ? 'tab-active' : ''}">VS Code</button> 
        <button on:click={() => handleTabSwitch("sublime")} class="tab w-1/2 {sublimeTabActive ? 'tab-active' : ''}">Sublime Text</button> 
    </div>
    
    <!-- Docs area -->
    <div class=" mt-10 text-center mx-auto">
        {#if vscodeTabActive}
            <VscodeComp />
        {:else}
            <SublimeComp />
        {/if}
    </div>
</div>

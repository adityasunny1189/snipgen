<script lang="ts">
    import { screenSizeStore } from "$lib/snipgen.store";


</script>

<div data-theme="black" class="navbar p-4 bg-base-100">
    <div class="flex-1">
      <a class="btn btn-ghost normal-case text-4xl">SnipGen</a>
    </div>
    {#if $screenSizeStore > 800}
        <div class="flex-none">
        <ul class="menu menu-horizontal text-lg px-4">
            <li><a>Contribute</a></li>
            <li><a href="/learn">Docs</a></li>
        </ul>
        </div>
    {/if}
</div>

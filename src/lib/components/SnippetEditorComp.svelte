<script lang="ts">
    import Prism from 'prismjs';
    import 'prismjs/components/prism-go';

    let showToast: boolean = false;

    let triggerCommand: string = "";
    let description: string = "";
    let code: string = "";
    let snippetResponse: string = "";

    const copyCode = (code: string | undefined) => {
        if (code !== undefined) {
            navigator.clipboard.writeText(code);
            showToast = true;
            setTimeout(() => {
                showToast = false;
            }, 1000);
        }
    }

</script>

<div data-theme="dark" class=" container mx-auto shadow-[0_0px_30px_10px_rgba(255,255,255,0.3)] p-4 my-8 artboard artboard-horizontal">
    <div class=" flex flex-row">
        <!-- code and command Block -->
        <div class=" w-1/2">
            <!-- commands -->
            <div class=" flex flex-row">
                <div class=" w-1/2 mr-2">
                    <input bind:value={triggerCommand} type="text" placeholder="Trigger Command" class="input input-bordered w-full max-w-xs" />
                </div>
                <div class=" w-1/2">
                    <input bind:value={description} type="text" placeholder="Description" class="input input-bordered w-full max-w-xs" />
                </div>
            </div>
            <!-- code block -->
            <div class=" mt-2">
                <textarea bind:value={snippetResponse} class="textarea textarea-bordered w-full h-96" placeholder="Code goes here"></textarea>
            </div>
        </div>
        <div class="divider divider-horizontal" />


        <!-- Snippet Output Block -->
        <div class=" w-1/2">
            <!-- Editor Tabs -->
            <div class=" flex flex-row">
                <div class=" tab tab-bordered tab-active w-1/2 ">
                    VS Code
                </div>
                <div class=" tab tab-bordered w-1/2">
                    Sublime Text
                </div>
            </div>
            <!-- Snippet Output -->
            <div>
                <div class=" relative my-4">
                    {#if snippetResponse !== undefined}
                        <pre class="my-6 p-4 break-all h-96 overflow-y-auto overflow-x-auto bg-[#1e1e1e] text-white rounded-lg"><code class="language-go">{@html Prism.highlight(snippetResponse, Prism.languages.go)}</code></pre>
                        <button on:click={() => copyCode(snippetResponse)} class="absolute top-2 right-2 p-2 bg-[#1e1e1e] text-white rounded">
                            <i class="fa fa-clone"></i>
                        </button>
                    {/if}
                </div>
            </div>
        </div>
    </div>
</div>

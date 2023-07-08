<script lang="ts">
    import Prism from 'prismjs';
    import 'prismjs/components/prism-json';

    let showToast: boolean = false;

    let triggerCommand: string = "";
    let description: string = "";
    let code: string = "";
    let snippet: string = "";
    let vsCodeSnippet: string = `{
    "${triggerCommand}": {
        "prefix": "${triggerCommand}",
        "body": [
            ${code}
        ],
        "description": "${description}"
}`;

    let sublimeSnippet: string = `<snippet>
    <content><![CDATA[
${code}
    ]]></content>
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
    <tabTrigger>${triggerCommand}</tabTrigger>
    <!-- Optional: Set a scope to limit where the snippet will trigger -->
    <!-- <scope>source.python</scope> -->
    <description>${description}</description>
</snippet>`;

    let vscodeTabActive: boolean = true;
    let sublimeTabActive: boolean = false;

    const copyCode = (code: string | undefined) => {
        if (code !== undefined) {
            navigator.clipboard.writeText(code);
            showToast = true;
            setTimeout(() => {
                showToast = false;
            }, 1000);
        }
    }

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

    const vscodeCodeParser = (code : string) => {
        code = code.replaceAll("\"", "\\\"");
        let codeArray = code.split("\n");
        let codeString = "";
        for (let i = 0; i < codeArray.length; i++) {
            if (i === codeArray.length - 1) {
                codeString += `"${codeArray[i]}"`;
            } else {
                codeString += `"${codeArray[i]}",\n`;
            }
        }
        return codeString;
    }

    $: {
        console.log(code);
        vsCodeSnippet = `{
    "${triggerCommand}": {
        "prefix": "${triggerCommand}",
        "body": [
            ${vscodeCodeParser(code)}
        ],
        "description": "${description}"
}`;
        console.log(vsCodeSnippet);
        
        sublimeSnippet = `<snippet>
    <content><![CDATA[
${code}
    ]]></content>
    <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
    <tabTrigger>${triggerCommand}</tabTrigger>
    <!-- Optional: Set a scope to limit where the snippet will trigger -->
    <!-- <scope>source.python</scope> -->
    <description>${description}</description>
</snippet>`;
        console.log(sublimeSnippet);
        
        if(vscodeTabActive) {
            snippet = vsCodeSnippet;
        } else {
            snippet = sublimeSnippet;
        }
    }

</script>

<div data-theme="dark" class=" container mx-auto h-full shadow-[0_0px_30px_10px_rgba(255,255,255,0.3)] p-4 my-8 artboard artboard-horizontal">
    <div class=" flex h-full flex-row">
        <!-- code and command Block -->
        <div class=" w-1/2">
            <!-- commands -->
            <div class=" flex flex-row">
                <div class=" w-1/2 mr-4">
                    <input bind:value={triggerCommand} type="text" placeholder="Trigger Command" class="input input-bordered w-full max-w-xs" />
                </div>
                <div class=" w-1/2">
                    <input bind:value={description} type="text" placeholder="Description" class="input input-bordered w-full max-w-xs" />
                </div>
            </div>
            <!-- code block -->
            <div class=" h-full mt-8">
                <textarea bind:value={code} class="textarea textarea-bordered w-full h-5/6" placeholder="Code goes here"></textarea>
            </div>
        </div>
        <div class="divider divider-horizontal" />


        <!-- Snippet Output Block -->
        <div class=" w-1/2">
            <!-- Editor Tabs -->
            <div class=" flex flex-row">
                <div on:click={() => handleTabSwitch("vscode")} class=" tab tab-bordered {vscodeTabActive ? 'tab-active' : ''} w-1/2 h-12">
                    <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="40" height="40" viewBox="0 0 48 48">
                        <path fill="#29b6f6" d="M44,11.11v25.78c0,1.27-0.79,2.4-1.98,2.82l-8.82,4.14L34,33V15L33.2,4.15l8.82,4.14 C43.21,8.71,44,9.84,44,11.11z"></path><path fill="#0277bd" d="M9,33.896L34,15V5.353c0-1.198-1.482-1.758-2.275-0.86L4.658,29.239 c-0.9,0.83-0.849,2.267,0.107,3.032c0,0,1.324,1.232,1.803,1.574C7.304,34.37,8.271,34.43,9,33.896z"></path><path fill="#0288d1" d="M9,14.104L34,33v9.647c0,1.198-1.482,1.758-2.275,0.86L4.658,18.761 c-0.9-0.83-0.849-2.267,0.107-3.032c0,0,1.324-1.232,1.803-1.574C7.304,13.63,8.271,13.57,9,14.104z"></path>
                    </svg>
                </div>
                <div on:click={() => handleTabSwitch("sublime")} class=" tab tab-bordered {sublimeTabActive ? 'tab-active' : ''} w-1/2 h-12">
                    <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="40" height="40" viewBox="0 0 48 48">
                        <defs><linearGradient id="NX4qzaRknlkLIGuB5rRvAa_6RHskkZGRABM_gr1" x1="19.639" x2="28.361" y1="3.481" y2="44.519" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#636363"></stop><stop offset="1" stop-color="#444"></stop></linearGradient><linearGradient id="NX4qzaRknlkLIGuB5rRvAb_6RHskkZGRABM_gr2" x1="13" x2="35" y1="30.684" y2="30.684" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#ff9c0f"></stop><stop offset=".813" stop-color="#d67e00"></stop></linearGradient></defs><g data-name="Ð¡Ð»Ð¾Ð¹ 2"><rect width="36" height="36" x="6" y="6" fill="url(#NX4qzaRknlkLIGuB5rRvAa_6RHskkZGRABM_gr1)" rx="2"></rect><path fill="#1d1d1b" d="M14,39a2,2,0,0,1-2-2V31.1A2.5,2.5,0,0,1,13.4,28.825L19.131,27,13.4,25.175A1.993,1.993,0,0,1,12,23.269V16.731A1.993,1.993,0,0,1,13.4,14.825L33.4,8.1A2,2,0,0,1,36,10v6.265a1.993,1.993,0,0,1-1.4,1.906L28.869,20,34.6,21.825A1.993,1.993,0,0,1,36,23.731v6.538a1.993,1.993,0,0,1-1.4,1.906l-20,6.732A2,2,0,0,1,14,39ZM34,10,14,16.731v6.538L25.727,27,14,31.1V37l20-6.732V23.731L22.273,20,34,16.269Z" opacity=".05"></path><path d="M14,38.5A1.5,1.5,0,0,1,12.5,37V31.1a1.494,1.494,0,0,1,1.046-1.43L20.779,27l-7.233-2.3A1.493,1.493,0,0,1,12.5,23.269V16.731A1.493,1.493,0,0,1,13.546,15.3l20-6.728A1.5,1.5,0,0,1,35.5,10v6.265A1.493,1.493,0,0,1,34.454,17.7L27.221,20l7.233,2.3A1.493,1.493,0,0,1,35.5,23.731v6.538A1.493,1.493,0,0,1,34.454,31.7l-20,6.732A1.486,1.486,0,0,1,14,38.5ZM33.7,9.051l.152.476-20,6.728a.5.5,0,0,0-.349.476v6.538a.5.5,0,0,0,.349.476L24.078,27,13.849,30.623a.5.5,0,0,0-.349.477V37a.5.5,0,0,0,.205.4.489.489,0,0,0,.446.073l20-6.732a.5.5,0,0,0,.349-.476V23.731a.5.5,0,0,0-.349-.476L23.922,20l10.229-3.255a.5.5,0,0,0,.349-.476V10a.5.5,0,0,0-.651-.477Z" opacity=".07"></path><path fill="url(#NX4qzaRknlkLIGuB5rRvAb_6RHskkZGRABM_gr2)" d="M34.3,31.222l-20,6.732A1,1,0,0,1,13,37V31.1a1,1,0,0,1,.7-.952l20-6.732a1,1,0,0,1,1.3.953v5.9A1,1,0,0,1,34.3,31.222Z"></path><path fill="#ff9c0f" d="M33.7,9.051l-20,6.727a1,1,0,0,0-.7.953v6.538a1,1,0,0,0,.7.953l21.061,6.7a1.162,1.162,0,0,0,.216-.423A2.867,2.867,0,0,0,35,29.962V23.731a1,1,0,0,0-.7-.953L25.571,20,34.3,17.222a1,1,0,0,0,.7-.953V10A1,1,0,0,0,33.7,9.051Z"></path></g>
                    </svg>
                </div>
            </div>
            <!-- Snippet Output -->
            <div class=" h-full relative mt-8">
                {#key snippet}
                    <pre class="my-4 p-4 break-all h-5/6 overflow-y-auto overflow-x-auto bg-[#1e1e1e] text-white rounded-lg"><code class="language-json">{@html Prism.highlight(snippet, Prism.languages.json)}</code></pre>
                    <button on:click={() => copyCode(snippet)} class="absolute top-2 right-2 p-2 bg-[#1e1e1e] text-white rounded">
                        <i class="fa fa-clone"></i>
                    </button>
                {/key}
            </div>
        </div>
    </div>
</div>

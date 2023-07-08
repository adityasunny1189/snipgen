<script lang="ts">
    import SublimeImage from '$lib/assets/images/sublime.png';
    import SublimeSnipgenOp from '$lib/assets/images/SublimeSnipgenOp.png';

</script>

<div class=" text-center">
    <h1 class=" text-5xl mb-10 underline">Steps to create snippet in sublime text</h1>

    <p class=" text-2xl my-6">
        <span class=" underline">Step 1:</span> Open Sublime Text and click on 
        <span class=" bg-[#FF9800] text-white p-2">
            Tools 
            <i class="fa text-black fa-arrow-right" aria-hidden="true" />
            Developer
            <i class="fa text-black fa-arrow-right" aria-hidden="true"></i>
            New Snippet...
        </span>
    </p>

    <img src={SublimeImage} alt="Sublime Text 3" class="w-2/3 mx-auto" />

    <p class=" text-2xl my-6">
        <span class=" underline">Step 2:</span> Create snippet using Snipgen and paste it in the file and save it.
    </p>

    <img src={SublimeSnipgenOp} alt="Sublime Text 3" class="w-2/3 mx-auto" />

    <p class=" text-2xl my-6">
        <span class=" underline">Step 3:</span> Name the file with 
        <span class=" bg-[#FF9800] text-white p-2">.sublime-snippet</span>
        extension and you are ready to go.
    </p>

</div>

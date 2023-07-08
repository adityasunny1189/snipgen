<script lang="ts">
    import VscodeImageOne from '$lib/assets/images/VscodeStepOne.png';
    import VscodeImageTwo from '$lib/assets/images/VscodeStepTwo.png';
    import VscodeImageThree from '$lib/assets/images/VscodeStepThree.png';
    import VscodeImageSnipgenOp from '$lib/assets/images/VscodeSnipgenOp.png';


</script>

<div class=" text-center">
    <h1 class=" text-5xl mb-10 underline">Steps to create snippet in VS Code</h1>

    <p class=" text-2xl my-6">
        <span class=" underline">Step 1:</span> Open Vs Code and click on 
        <span class=" bg-[#0065A9] text-white p-2">
            Code 
            <i class="fa text-black fa-arrow-right" aria-hidden="true" />
            Settings
            <i class="fa text-black fa-arrow-right" aria-hidden="true"></i>
            Configure User Snippets
        </span>
    </p>

    <img src={VscodeImageOne} alt="Sublime Text 3" class="w-2/3 mx-auto" />

    <p class=" text-2xl my-6">
        <span class=" underline">Step 2:</span> Click on  
        <span class=" bg-[#0065A9] text-white p-2">
            New Global Snippets file...
        </span>
    </p>

    <img src={VscodeImageTwo} alt="Sublime Text 3" class="w-2/3 mx-auto" />

    <p class=" text-2xl my-6">
        <span class=" underline">Step 3:</span> Give a name to the file and click  
        <span class=" bg-[#0065A9] text-white p-2">
            enter
        </span>
    </p>

    <img src={VscodeImageThree} alt="Sublime Text 3" class="w-2/3 mx-auto" />

    <p class=" text-2xl my-6">
        <span class=" underline">Step 4:</span> Create snippet using Snipgen and paste it in the file and save it.  
    </p>

    <img src={VscodeImageSnipgenOp} alt="Sublime Text 3" class="w-2/3 mx-auto" />

    <p class=" text-2xl my-6">
        <span class=" underline">Step 5:</span> You are ready to go. Now you can use the snippet in your code.
    </p>

</div>

<script>
import Button from "./Button.svelte";

    export let darkMode;
// variables
    let step = 1;
    let imgs = ["src/assets/loading.svg", "src/assets/validated_dark.svg"];
// fonctions
    const nextStep = () => {
        if (step < 4) {
            step ++;
        }
    }

    const backStep = () => {
        if (step > 1) {
            step --;
        }
    }
</script>

<section class={darkMode ? 'steps-light' : 'steps-dark'}>
    <div class="steps">
        <!-- step1 -->
        {#if step === 1}
        <div class="step load">
            <div class="line"></div>
            <span>
                <img src={imgs[0]} alt="Mon image" width="20px">
            </span>
            <span>
                Step 1
            </span>
        </div>
        {:else}
        <div class="step good">
            <div class="line"></div>
            <span>
                <img src={imgs[1]} alt="Mon image" width="20px">
            </span>
            <span>
                Step 1
            </span>
        </div>
        {/if}

    <!-- step 2 -->
        {#if step < 2}
            <div class="step">
                    <div class="line"></div>
                    <p>
                        Step 2
                    </p>
            </div>

        {:else if step === 2}
        <div class="step load">
            <div class="line"></div>
            <span>
                <img src={imgs[0]} alt="Mon image" width="20px">
            </span>
            <span>
                Step 2
            </span>
        </div>
        {:else}
        <div class="step good">
            <div class="line"></div>
            <span>
                <img src={imgs[1]} alt="Mon image" width="20px">
            </span>
            <span>
                Step 2
            </span>
        </div>
        {/if}

    <!-- step 3 -->

        {#if step < 3}
        <div class="step">
            <div class="line"></div>
            <span>
                Step 3
            </span>
        </div>

        {:else if step === 3}
        <div class="step load">
            <div class="line"></div>
            <span>
                <img src={imgs[0]} alt="Mon image" width="20px">
            </span>
            <span>
                Step 3
            </span>
        </div>

        {:else}
        <div class="step good">
            <div class="line"></div>
            <span>
                <img src={imgs[1]} alt="Mon image" width="20px">
            </span>
            <span>
                Step 3
            </span>
        </div>
        {/if}
    </div>
    <div class="buttons">
        <Button darkMode={darkMode} on:click={ backStep }>
            Etape précédente
        </Button> 
        <Button darkMode={darkMode} on:click={ nextStep }>
            Etape suivante
        </Button> 
    </div>
</section>

<!--
        <div on:click={ backStep }>
            <Button darkMode={darkMode}>
                Etape précédente
            </Button> 
        </div>
        <div on:click={ nextStep }>
            <Button darkMode={darkMode}>
                Etape suivante
            </Button> 
        </div>
-->


<style>
    section{
        border-radius: 24px;
        padding: 20px;
    }

    .steps-light{
        background-color: #F2F2F2;;
    }

    .steps-dark{
        background-color: #141316;
    }

    .steps{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        margin-left: 5%;
        height: 15%;
        color: #9F9F9F;
    }

    .buttons{
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        margin-top: 10%;
        column-gap: 10px;
    }

    .line{
        width: 80%;
        height: 1%;
        background-color: #9F9F9F;
        margin-bottom: 5%;
    }

    .load{
        color: darkorange;
        
    }

    .load > .line{
        background-color: darkorange;
    }
    
    .good{
        color: #7DCBA4;
    }

    .good > .line{
        background-color: #7DCBA4;
    }


    
</style>
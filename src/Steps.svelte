<script>
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

<section class="steps">
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
</section>
<section class="buttons">
    <button on:click={ backStep }>
        Etape précédente
    </button> 
    <button on:click={ nextStep }>
        Etape suivante
    </button> 
</section>
{step}


<style>
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
        color: #9F9F9F
    }

    button {
        border-radius: 8px;
        border: 1px solid transparent;
        padding: 0.6em 1.2em;
        margin: 3%;
        font-size: 1em;
        font-weight: 500;
        font-family: inherit;
        background-color: #DBEBE3;
        cursor: pointer;
        transition: border-color 0.25s;
        color: #929098;
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
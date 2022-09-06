<script>
// variables
    let number = 1;
    let numberValidate = false;
    let codeValidate = false;
    let code = [9, 8, 7, 6, 5, 4, 3, 2, 1, 0];
    //let selectCode;

// fonctions
    // choix nombre
    const supNumber = () => {
        if(number < 10){
            number ++;
        }
    };

    const subNumber = () => {
        if(number > 1){
            number --;
        }
    };

    // validation nombre
    const sizeTable = () => {
        let selectCode = new Array(number);
        console.log(selectCode);
        for(let i = 0; i < selectCode.length; i++){
            selectCode[i] = code[i];
        }
        console.log(selectCode);

    }

    const validateChoiceNumber = () => {
        numberValidate = true;
        sizeTable();
    };

    const disableValidateChoiceNumber = () => {
        numberValidate = false;
    }

    // validation confirmation
    const validateCode = () => {
        codeValidate = true;
    }

</script>

{#if numberValidate === false}
    <p>Choisissez le nombre de case de code de vérification</p>

    <div>
        <button on:click={ supNumber }>
            +
        </button>
        
        <p>{number}</p>
        
        <button on:click={ subNumber }>
            -
        </button>
        
    </div>
    <button on:click={ validateChoiceNumber }>
        Valider
    </button>
{/if}


{#if numberValidate === true && codeValidate === false }

    <p>Chiffre / nombre retenu : { number }</p>

    {#each Array(number) as _, i}
        <div>
            <button on:click={ supNumber }>
                +
            </button>
            
            <p>test</p> 
            
            <button on:click={ subNumber }>
                -
            </button> 
        </div>        
    {/each}

    <button on:click={ validateCode }>
        Valider
    </button>

    <button on:click={ disableValidateChoiceNumber }>
        Retour en arrière
    </button>
{/if}








{#if codeValidate === true}
    <p>Félicitations, le code a bien été validé !</p>
{/if}

<style>

</style>
<script>
// variables
    let number = 1;
    let numberValidate = false;

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
    const validateChoiceNumber = () => {
        numberValidate = true;
    };

    const disableValidateChoiceNumber = () => {
        numberValidate = false;
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


{#if numberValidate === true}
    <p>Chiffre / nombre retenu : { number }</p>
    <button on:click={ disableValidateChoiceNumber }>
        Retour en arrière
    </button>
{/if}

<style>

</style>
<script>
    // variables
        let number = 1;
        let numberValidate = false;
        let codeValidate = false;
        let code = [9, 8, 7, 6, 5, 4, 3, 2, 1, 0];
        let selectCode;
    
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
            selectCode = new Array(number);
            console.log(selectCode);
            for(let i = 0; i < selectCode.length; i++){
                selectCode[i] = code[i];
            }
            code.splice(selectCode.length);
        }
    
        const validateChoiceNumber = () => {
            sizeTable();
            numberValidate = true;
        };
    
        const disableValidateChoiceNumber = () => {
            code = [9, 8, 7, 6, 5, 4, 3, 2, 1, 0];
            numberValidate = false;
        }
    
        // validation confirmation
        const supNumberCode = (i) => {
            if( selectCode[i] < 9 ){
                selectCode[i] ++;
            } 
        }
    
        const subNumberCode = (i) => {
            if ( selectCode[i] > 0 ) {
                selectCode[i] -= 1;
            }
    
        }
    
        const validateCode = () => {
            if ( JSON.stringify(selectCode) === JSON.stringify(code) ) {
                codeValidate = true;
            }
        }
    
    </script>
    
    
    {#if numberValidate === false}
        <p>Choisissez le nombre de case de code de vérification</p>
    
        <div>
            <button on:click={ subNumber }>
                -
            </button>
            <input type="number" bind:value="{number}" id="">
            <button on:click={ supNumber }>
                +
            </button>
            
        </div>
        <button on:click={ validateChoiceNumber }>
            Valider
        </button>
    {/if}
    
    
    {#if numberValidate === true && codeValidate === false }
    
        <p>Chiffre / nombre retenu : { number }</p>
        <div class="code">
        {#each Array(number) as _, i}
            <div class="chiffre">
                
                <button on:click={ 
                    (() => {
                        subNumberCode(i);
                    })
                }>
                    -
                </button> 

                <span>
                    <input type="number" value={selectCode[i]}>
                </span>

                <button on:click={ 
                     (() => {
                        supNumberCode(i);
                        })
                    }>
                        +
                    </button>
            </div>        
        {/each}
        </div>
    
        <div>
            Code : 
        </div>
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







    /* Retrait flèches input */

        /* Firefox */
        input[type=number] {
            -moz-appearance: textfield;
        }
        
        /* Chrome */
        input::-webkit-inner-spin-button,
        input::-webkit-outer-spin-button { 
            -webkit-appearance: none;
            margin:0;
        }
        
        /* Opéra*/
        input::-o-inner-spin-button,
        input::-o-outer-spin-button { 
            -o-appearance: none;
            margin:0
}
    </style>
<script>
    import Button from "./Button.svelte";
    export let darkMode;
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
    
    <section class={darkMode ? 'inputNumber-light' : 'inputNumber-dark'}>
    {#if numberValidate === false}
        <p>Choisissez le nombre de case de code de vérification</p>
    
        <div>
            <button class={darkMode ? 'button-dark' : 'button-light'} on:click={ subNumber }>
                -
            </button>
            <input type="number" bind:value="{number}" id="">
            <button class={darkMode ? 'button-dark' : 'button-light'} on:click={ supNumber }>
                +
            </button>
            
        </div>
        <div on:click={ validateChoiceNumber }>
            <Button darkMode={darkMode}>
                Valider
            </Button>
        </div>
    {/if}
       
    {#if numberValidate === true && codeValidate === false }
    
        <p>Chiffre / nombre retenu : { number }</p>
        <div class="code">
        {#each Array(number) as _, i}
            <div class="chiffre">
                
                <button class={darkMode ? 'button-dark' : 'button-light'} on:click={ 
                    (() => {
                        subNumberCode(i);
                    })
                }>
                    -
                </button> 

                <span>
                    <input type="number" value={selectCode[i]}>
                </span>

                <button class={darkMode ? 'button-dark' : 'button-light'} on:click={ 
                     (() => {
                        supNumberCode(i);
                        })
                    }>
                        +
                    </button>
            </div>        
        {/each}
        </div>
    
        <div class="display_validation">
            <br>
            Code : 
            <br>
            <br>
            <div on:click={ validateCode }>
                <Button darkMode={darkMode}>
                    Valider
                </Button>
            </div>
            
            <div on:click={ disableValidateChoiceNumber }>
                <Button darkMode={darkMode}>
                    Retour en arrière
                </Button>
            </div>
        </div>
    {/if}
    
    {#if codeValidate === true}
        <p>Félicitations, le code a bien été validé !</p>
    {/if}

    </section>
    
    <style>

        section{
            border-radius: 24px;
            padding: 20px;
        }

        .inputNumber-light{
            background-color: #F2F2F2;;
        }

        .inputNumber-dark{
            background-color: #001014;
        }

        .display_validation div{
            display: inline-block;
        }

        .button-light {
            background-color: rgba(0,220,130,1);
            color: black;
            transition: 0.4s all ease-in-out;
            margin: 5px;
        }
    
        .button-dark {
            background-color: #00181E;
            color: #E6FCF3;
            transition: 0.3s all ease-in-out;
            margin: 5px;
        }

        .chiffre{
            margin-bottom: 10px;
        }

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
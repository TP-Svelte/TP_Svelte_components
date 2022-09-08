<script>
let input = '';
let data = ''
let isDataValid = false;
export let darkMode;

const search  = async () => {
     isInputEmpty();

     if (!isDataValid){
         data = '';
         const response = await fetch('https://api-adresse.data.gouv.fr/search/?q=' + input )
         data = await response.json()
     }
 }

 const isInputEmpty = () => {
     if (input == '' && isDataValid){
         return isDataValid = false;
     }
 }

const updateInput = (key) => {
    input = data.features[key].properties.label
    data = '';
    isDataValid = true;
}

const resetInput = () => {
    input = '';
    data = '';
}

function debounce(func, timeout = 300){
   let timer;
   return (...args) => {
     clearTimeout(timer);
     timer = setTimeout(() => { func.apply(this, args); }, timeout);
   };
 }
</script>


<div class='container'>
    <div>

    <input type="text" placeholder="Address" class:is-active={isDataValid} bind:value={input} on:input={debounce(() => search())} class={darkMode ?  'input-light' : 'input-dark'}/> 

    <div id='deleteBtn' on:click={resetInput}></div>
    
    {#if data}
        <ul>
            {#each Object.entries(data.features) as _, i}
                <li on:click={(() => updateInput(i))} class={darkMode ?  'li-light' : 'li-dark'}>
                    {data.features[i].properties.label}
                </li>
            {/each}
        </ul>
    {/if}
    </div>  
</div>


<style> 

.container {
    padding: 18px 3%;
    width: 500px;
    border-radius: 24px;
}

input {
    padding-left: 20px;
    margin-right: 0px;
    display: block;
    width: 100%;
    height: 50px;
    border-radius: 15px;
    border: none;
    font-weight: 400;
    font-size: 18px;
}

.input-light {
    background-color: #F2F2F2;
    color: #9F9F9F;

}

.input-dark {
    background-color:#E6FCF3;
    color: black;

}

input:focus{
    outline: none;
}

input.is-active {
     border: 2px solid #7DCBA4;
 }

li {
    padding-left: 20px;
    width: 100%;
    cursor: pointer;
    list-style: none;
    font-weight: 400;
    font-size: 16px;
    padding-top: 4px;
    padding-bottom: 4px;
}

.li-light {
    background-color: white;
    color: #BCBCBC;
}

.li-dark {
    background-color: #E6FCF3;
    color: black;
}

.li-dark:hover {
    background-color: #001014;
    color: #00DC82;
}

li:hover {
    background-color: #DBEBE3;
}

li:last-child {
    border-radius: 0px 0px 4px 4px;
}

ul {
    display: block;
    width: 100%;
    margin-top: -32px;
    padding-top: 20px;
    padding-left: 0px;    
}

</style>



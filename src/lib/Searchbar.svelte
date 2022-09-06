<script>
let input = '';
let data = ''

const search  = async () => {
    const response = await fetch('https://api-adresse.data.gouv.fr/search/?q=' + input )
    data = await response.json()
}

const updateInput = (key) => {
    input = data.features[key].properties.label
}

const resetInput = () => {
    input = '';
    data = '';
}
</script>


<input type="text" placeholder="Adresse" bind:value={input} on:input={search}/> 
<button on:click={resetInput}>Effacer</button>

<span>
    {#if data}
        <ul>
            {#each Object.entries(data.features) as _, i}
                <li on:click={(() => updateInput(i))}>
                    {data.features[i].properties.label}
                </li>
            {/each}
        </ul>
    {/if}

    
</span>



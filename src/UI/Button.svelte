<script>
    export let darkMode;



</script>

<button  class={darkMode ?  'button-dark' : 'button-light'}>            
    {#if darkMode == true}
    Dark mode
    {:else}
    Light mode
    {/if}
</button>


<style>
    .button-light {
        background-color: #DBEBE3;
        color: #929098;
        transition: 0.4s all ease-in-out;
    }
    .button-dark {
        background-color: #27262D;
        color: #DBEBE3;
        transition: 0.3s all ease-in-out;

    }
</style>
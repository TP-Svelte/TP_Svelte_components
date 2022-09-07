<script>
    export let darkMode;

</script>

<button class={darkMode ?  'button-dark' : 'button-light'}>Ajouter au panier</button>


<style>
    .button-light {
        background-color: #DBEBE3;
        color: #929098;
    }
    .button-dark {
        background-color: #27262D;
        color: #DBEBE3;
    }
</style>
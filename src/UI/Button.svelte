<script>
    export let darkMode;
</script>

<button  class={darkMode ?  'button-dark' : 'button-light'}>            
    <slot/>
</button>


<style>
    .button-light {
        background-color: rgba(0,220,130,1);
        color: black;
        transition: 0.4s all ease-in-out;
    }
    .button-dark {
        background-color: #00181E;
        color: #E6FCF3;
        transition: 0.3s all ease-in-out;

    }
</style>
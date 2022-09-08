<script>
    export let darkMode;
    import Button from "./Button.svelte";
    
    const deploy = () => {
        document.getElementById("hidden_modal").style.display = "block";
        setTimeout("document.getElementById('hidden_modal').style.display = 'none'",3000);
    }
</script>

<div id="Toast" class={darkMode ? 'toast-light' : 'toast-dark'} on:click={ deploy }>
    <Button darkMode={darkMode}>
        <slot name="button"/>
    </Button>
    <div id="hidden_modal" class={darkMode ? 'toast-light' : 'toast-dark'} >
        <h3><slot name="modal_title"/></h3>
        <p><slot name="modal_text"/></p>
    </div>
</div>

<style>
    #Toast{
        padding: 50px;
        border-radius: 24px;
    }

    .toast-light{
        background-color: #F2F2F2;
    }

    .toast-dark{
        background-color: #001014;
    }

    #Toast h3{
        color: #7DCBA4;
        margin-left: 20px;
        margin-top: 0;
    }

    #Toast h3::before{
        content: url(src/assets/validated_dark.svg);
        width: 20%;
        height: 20px;
        display: block;
        transform: scale(.2);
        position: relative;
        bottom: -14px;
        left: 30px;
    }
    
    #Toast p{
        color: #9F9F9F;
    }

    #Toast button{
        background-color: #DBEBE3;
        color: #9F9F9F;
    }

    #hidden_modal{
        display: none;
        z-index: 1;
        padding: 10px 20px;
        width: 300px;
        border-radius: 24px;
        box-shadow: 3px 7px 15px 1px #898989;
        position: fixed;
        bottom: 20px;
        right: 20px;
    }
</style>
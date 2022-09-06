<script>
    const deploy = () => {
        document.getElementById("hidden_modal").style.display = "block";
        setTimeout("document.getElementById('hidden_modal').style.display = 'none'",3000);
    }
</script>

<div id="Toast" on:click={ deploy }>
    <button>
        <slot name="button"/>
    </button>
    <div id="hidden_modal">
        <h3><slot name="modal_title"/></h3>
        <p><slot name="modal_text"/></p>
    </div>
</div>

<style>
    #Toast{
        margin: 50px;
        background-color: #F2F2F2;
        padding: 50px;
        border-radius: 24px;
    }

    #Toast h3{
        color: #DBEBE3;
        margin-left: 20px;
        margin-top: 0;
    }

    #Toast h3::before{
        content: url(src/assets/validated.svg);
        width: 20%;
        height: 20px;
        display: block;
        transform: scale(.2);
        position: relative;
        bottom: -14px;
        left: 12px;
    }
    
    #Toast p{
        color: #9F9F9F;
    }

    #Toast button{
        background-color: #DBEBE3;
    }

    #hidden_modal{
        display: none;
        z-index: 1;
        box-shadow: 3px 7px 15px 1px #898989;
        position: absolute;
        bottom: 20px;
        right: 20px;
        background: white;
        padding: 10px 20px;
        width: 300px;
        border-radius: 24px;
    }
</style>
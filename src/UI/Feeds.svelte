<script>  
    export let checkpoints;

    const sent_img = "src/assets/sent.svg";
    const loading_img = "src/assets/loading.svg";
    const closed_img = "src/assets/closed.svg";
    const validated_img = "src/assets/validated.svg";
</script>

<div id="checkpoints">
    {#each checkpoints as checkpoint}
        <div>
            {#if checkpoint[1] === "sent"}
              <img src="{sent_img}" alt="sent icon">
            {:else if checkpoint[1] === "loading" }
              <img src="{loading_img}" alt="loading icon">
            {:else if checkpoint[1] === "closed"}
              <img src="{closed_img}" alt="closed icon">
            {:else}
              <img src="{validated_img}" alt="validated icon">
            {/if}
            <p>{checkpoint[0]}</p>
            <p>{checkpoint[2]}</p>
        </div>
    {/each}
</div>

<style>
    #checkpoints{
        margin: 50px;
        background-color: #F2F2F2;
        padding: 50px;
        border-radius: 24px;
    }

    #checkpoints div{
        display: flex;
        flex-wrap: wrap;
        width: 450px;
        justify-content: space-between;
        position: relative;
    }

    #checkpoints div:not(:last-child){
        margin-bottom: 50px;
    }

    #checkpoints div:not(:last-child):before{ 
        content: url(src/assets/line.svg) ;
        position: absolute; 
        left: 23px;
        bottom: -45px;
    }

    #checkpoints img{
        width: 50px;
    }
    
    #checkpoints p{
        color: #9F9F9F;
    }
        
    #checkpoints div p:nth-child(2){
        font-weight: 700;
    }

</style>

<script>  
    export let checkpoints;
    export let darkMode;

    const sent_img = "src/assets/sent.svg";
    const loading_img = "src/assets/loading.svg";
    const closed_img = "src/assets/closed.svg";
    const validated_img = "src/assets/validated.svg";
</script>

<div id="Feeds" class={darkMode ?  'feeds-light' : 'feeds-dark'}>
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
    #Feeds{
        padding: 50px;
        border-radius: 24px;
    }

    .feeds-light{
        background-color: #F2F2F2;
    }

    .feeds-dark{
        background-color: #001014;
    }

    #Feeds div{
        display: flex;
        flex-wrap: wrap;
        width: 100%;
        justify-content: space-between;
        position: relative;
    }

    #Feeds div:not(:last-child){
        margin-bottom: 50px;
    }

    #Feeds div:not(:last-child):before{ 
        content: url(src/assets/line.svg);
        position: absolute; 
        left: 23px;
        bottom: -45px;
    }

    #Feeds img{
        width: 50px;
    }
    
    #Feeds p{
        color: #9F9F9F;
    }
        
    #Feeds div p:nth-child(2){
        font-weight: 700;
    }

    @media (max-width: 900px) {
        #Feeds div:not(:last-child):before{ 
            left: auto;
        }

        #Feeds div{
            justify-content: center;
        }
           
        #Feeds div p:nth-child(2){
            width: 100%;
            margin-bottom: 0;
        }
    }

</style>


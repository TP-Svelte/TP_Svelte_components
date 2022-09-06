<script>  
    export let checkpoints;

    const sent_img = "src/assets/sent.svg";
    const loading_img = "src/assets/loading.svg";
    const closed_img = "src/assets/closed.svg";
    const validated_img = "src/assets/validated.svg";
</script>

<div>
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

</style>
<script>
// variables
    let homePage = true;
    let codePage = false;
    let finishPage = false;

// fonctions

</script>

<section>
    <div class="homePage">
        <!-- {#if homePage === true} -->
        <div class="line"></div>
        <p>
            Step 1
        </p>
        <p>
            Choix de la taille du code
        </p>
        <!-- {/if} -->

    </div>
    <div class="codePage">
        <!-- {#if codePage === true} -->
            <div class="line"></div>
            <p>
                Step 2
            </p>
            <p>
                Entrée du code de sécurité
            </p>
        <!-- {/if} -->

    </div>
    <div class="finishPage">
        <!-- {#if finishPage === true} -->
        <div class="line"></div>
        <p>
            Step 3
        </p>
        <p>
            Page de fin
        </p>
    
        <!-- {/if} -->

    </div>


</section>



<style>
    
</style>
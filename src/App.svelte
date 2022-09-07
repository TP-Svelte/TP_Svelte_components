<script>

    import UserCard from "./UI/UserCard.svelte";
    import Dropdown from "./UI/Dropdown.svelte";
    import Feeds from "./UI/Feeds.svelte";
    import Toast from "./UI/Toast.svelte";
    import Searchbar from "./UI/Searchbar.svelte";
    import Button from "./UI/Button.svelte";
    import Reviews from "./UI/Reviews.svelte"
    import Header from "./components/Header.svelte"

    let persons = [{
        name: 'Maxime',
        cover: 'https://images.unsplash.com/photo-1657664065994-5e257c88b7f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1683&q=800'
    },
        {name: 'Jul',
        cover: 'https://images.unsplash.com/photo-1662425877955-1092c2e1309e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1771&q=80'
    },
        {name: 'Jul',
        cover: 'https://images.unsplash.com/photo-1657664065994-5e257c88b7f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1683&q=80'
    },
    ]
    
      
    let checkpoints_list = [
      [ "Case submitted", "sent", "2 sept" ],
      [ "Case being processed", "loading", "2 sept" ],
      [ "Case refused", "closed", "5 sept" ],
      [ "Case under reassessment", "loading", "6 sept"],
      [ "Case accepted", "validated", "15 sept" ]    
    ];

    // REVIEWS
    let reviewsInfo = [
        {
        name: 'Valentin',
        title: "Can't say enough goog things",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam nemo aperiam, eveniet omnis, delectus magni re",
        stars: 5
    }]

    let darkMode = true
    const toggleMode = () => {
        darkMode = !darkMode
    }
</script>



<!-- <div class="container"> -->
<Header />
<div on:click={toggleMode}>
    <Button darkMode={darkMode}>
        {#if darkMode == true}
            Dark mode
        {:else}
            Light mode
        {/if}
    </Button>
</div>
<div class="flex">
    <div>
        <Toast darkMode={darkMode}>
            <span slot="button">
                Add to calendar
            </span>

            <span slot="modal_title">
                Event added
            </span>

            <span slot="modal_text">
                Now, you can find this event in your calendar.
            </span>
        </Toast>
    </div>
    <div class="doc">
        <h2>Toast</h2>
        <p> La création d'un toast passe par des slots. <br>
            Pour créer son Toast : 
            <li>passer le nom du bouton souhaité dans le span slot="button"</li>
            <li>passer le titre de la modale qui apparait au clic dans le span slot="modal_title"</li>
            <li>passer le texte de la modale qui apparait au clic dans le span slot="modal_text"</li>
        </p>

    </div>
</div>
<div class="flex">
    <div>
        <Feeds darkMode={darkMode} checkpoints={checkpoints_list} />
    </div>
    <div class="doc">
        <h2>Feeds</h2>
        <p>
            Pour créer ses Feeds : 
            passer ses valeurs en array dans la variable checkpoints_list sous le format [ "text", "status", "date" ].
            <br>Les status disponsibles sont : sent, loading, closed, validated.
            <br>Chaque status est lié à une icône. 
        </p>
    </div>
</div>

<div class="flex">
    <div>
        <UserCard darkMode={darkMode} persons={persons} />
    </div>
    <div class="doc">
        <h2>User card</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex reviews">
        <Reviews darkMode={darkMode} reviewsInfo={reviewsInfo}></Reviews> 
    <div class="doc  reviews">
        <h2>Reviews</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex">
    <div>
        <Dropdown />
    </div>
    <div class="doc">
        <h2>Dropdown</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex">
    <div>
        <Searchbar></Searchbar>
    </div>
    <div class="doc">
        <h2>Adress Searchbar</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>


<!-- <Reviews darkMode={true} reviewsInfo={reviewsInfo}></Reviews>  -->

<!-- </div> -->

<div on:click={toggleMode}>
    <Button darkMode={darkMode}>
        {#if darkMode == true}
            Dark mode
        {:else}
            Light mode
        {/if}
    </Button>
</div>

<style>
    * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    }
        
    body {
        overflow-y: hidden;

    }

    .container {
        width: 100vw;
    }

    .flex {
        display: flex;
        /* width: 100vw; */
        justify-content: center;
        align-items: center;
        padding: 30px;
        gap: 50px
    }

    .flex > div {
        width: 50%;
    }

    .doc > h2 {
        margin-bottom: 1em;
        color: black;
    }
    .doc > p {
        margin-bottom: 2em;
        color: black;

    }

    .doc {
        text-align: left;
    }

</style>
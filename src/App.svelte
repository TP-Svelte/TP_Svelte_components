<script>
    import InputNumber from "./UI/InputNumber.svelte";
    import Steps from "./UI/Steps.svelte";
    import UserCard from "./UI/UserCard.svelte";
    import Dropdown from "./UI/Dropdown.svelte";
    import Feeds from "./UI/Feeds.svelte";
    import Toast from "./UI/Toast.svelte";
    import Searchbar from "./UI/Searchbar.svelte";
    import Button from "./UI/Button.svelte";
    import Reviews from "./UI/Reviews.svelte"
    import Header from "./components/Header.svelte"

    let persons = [{
        name: 'Chloé',
        cover: 'https://images.unsplash.com/photo-1657664065994-5e257c88b7f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1683&q=800'
    },
        {name: 'Nico',
        cover: 'https://images.unsplash.com/photo-1662425877955-1092c2e1309e?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1771&q=80'
    },
        {name: 'Doriane',
        cover: 'https://images.unsplash.com/photo-1657664065994-5e257c88b7f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1683&q=80'
    },
    ]
    
      
    let checkpoints_list = [
      [ "Dossier envoyé", "sent", "2 sept" ],
      [ "Dossier en cours de traitement", "loading", "2 sept" ],
      [ "Dossier refusé", "closed", "5 sept" ],
      [ "Dossier en cours de réévaluation", "loading", "6 sept"],
      [ "Dossier accepté", "validated", "15 sept" ]    
    ];

    // REVIEWS
    let reviewsInfo = [
        {
        name: 'Valentin',
        title: "Can't say enough goog things",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam nemo aperiam, eveniet omnis, delectus magni re",
        stars: 5
    },
        {
        name: 'Valentin',
        title: "Can't say enough goog things",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam nemo aperiam, eveniet omnis, delectus magni re",
        stars: 1
    },
]
	let red = 0;
	let green = 0;
	let blue = 0;

	let rootElement;
    let darkMode = true
    $: rootElement && rootElement.style.setProperty('--container-background', `rgb(${red}, ${green}, ${blue})`);

    const toggleMode = () => {
        darkMode = !darkMode
        document.body.classList.toggle('is-dark')

    }
</script>



<Steps/> 
<InputNumber/> 


<div class="container">
<Header darkMode={darkMode} />
<div on:click={toggleMode}>
    <Button darkMode={darkMode} />
</div>
<div class="flex">
    <div >
        <!-- 
            Pour créer son Toast : 
            - mettre le nom du bouton dans le <span slot="button">
            - mettre le titre de la modale qui apparait au clic dans <span slot="modal_title">
            - mettre le texte de la modale qui apparait au clic dans <span slot="modal_text">  
        -->
        <Toast>
            <span slot="button">
                Ajouter à l'agenda
            </span>

            <span slot="modal_title">
                Evènement ajouté
            </span>

            <span slot="modal_text">
                Vous pouvez retrouver cet évènement dans votre agenda
            </span>
        </Toast>
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Toast</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>

    </div>
</div>
<div class="flex">
    <div class="hover-ui">
        <!-- 
            Pour créer ses Feeds : 
            donner ses valeurs dans la variable checkpoints_list sous le format [ "text", "status", "date" ].
            Les status disponsibles sont : sent, loading, closed, validated.
        -->
        <Feeds checkpoints={checkpoints_list} />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Feeds</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <UserCard darkMode={darkMode} persons={persons} />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>User card</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="reviews">
    <div class="hover-ui">       
         <Reviews  darkMode={darkMode} reviewsInfo={reviewsInfo}></Reviews> 
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Reviews</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex">
    <div>
        <Dropdown />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Dropdown</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <Searchbar></Searchbar>
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Adress Searchbar</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>


<!-- <Reviews darkMode={true} reviewsInfo={reviewsInfo}></Reviews>  -->

</div>

<div on:click={toggleMode}>
    <Button darkMode={darkMode} />
</div>

<style>

    * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    }
    :global(.is-dark) {
        background-color: #00181E;
        transition: 0.3s argb(19, 19, 19)se-in-out;
    }

.container {
    margin-top: 5em;


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
        color: #001014;
        transition: 0.3s all ease-in-out;

    }

    .doc-dark > h2 {
        margin-bottom: 1em;
        color: rgba(0,220,130,1);
        transition: 0.3s all ease-in-out;

    }

    .doc > p {
        margin-bottom: 2em;
        color: #001014;
        transition: 0.3s all ease-in-out;


    }
    .doc-dark > p {
        margin-bottom: 2em;
        color: #E6FCF3;
        transition: 0.3s all ease-in-out;


    }

    .doc {
        text-align: left;
        transition: 0.3s all ease-in-out;

    }

    .doc-dark {
        text-align: left;
        transition: 0.3s all ease-in-out;

    }
    .reviews {
        width: 100%;
    }
    .reviews > .doc {
        padding-left: 2em;
        width: 70%;

    }
    .reviews > .doc-dark {
        padding-left: 2em;
        width: 70%;

    }
.hover-ui {
    transition: 0.3s all ease-in-out;

}
.hover-ui:hover {
    transform:translateY(-20px);
    cursor: pointer;

}
</style>
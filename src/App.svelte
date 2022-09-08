<script>
    import InputNumber from "./UI/InputNumber.svelte";
    import Steps from "./UI/Steps.svelte";
    import UserCard from "./UI/UserCard.svelte";
    import Dropdown from "./UI/Dropdown.svelte";
    import Navbar from "./UI/Navbar.svelte";
    import Feeds from "./UI/Feeds.svelte";
    import Toast from "./UI/Toast.svelte";
    import Searchbar from "./UI/Searchbar.svelte";
    import Button from "./UI/Button.svelte";
    import Reviews from "./UI/Reviews.svelte"
    import Carousel from "./UI/Carousel.svelte"
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
        stars: 4.5
    },
        {
        name: 'Valentin',
        title: "Can't say enough goog things",
        description: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam nemo aperiam, eveniet omnis, delectus magni re",
        stars: 1
    },
]


    let darkMode = true

    const toggleMode = () => {
        darkMode = !darkMode
        document.body.classList.toggle('is-dark')

    }


    const images = [
        {image_url: "https://images.unsplash.com/photo-1657664057951-17679442315d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1674&q=80", id: "image1"},
        {image_url: "https://images.unsplash.com/photo-1662437447166-4ba78953f24f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80", id: "image2"}, 
        {image_url: "https://images.unsplash.com/photo-1662398819908-507ae18bf21f?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2832&q=80", id: "image3"}, 
        {image_url: "https://images.unsplash.com/photo-1662368356341-9a9a8a9b1883?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2070&q=80", id: "image4"}, 
        {image_url: "https://images.unsplash.com/photo-1662307502412-70e5b5ff2c32?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1480&q=80", id: "image5"}, 
        {image_url: "https://images.unsplash.com/photo-1662384874972-cacf00a9e013?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2071&q=80", id: "image6"},
    ]
</script>





<div class="container">
<Header darkMode={darkMode} />
<div class="button-up" on:click={toggleMode}>
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
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Toast</h2>
        <p> Le toast permet d'afficher une modale de 3 secondes en bas de l'écran avec le texte souhaité au clic sur le bouton.  
            <br>
            La création d'un toast passe par des slots. 
	    <br>
            Pour créer son Toast : 
            <li>passer le nom du bouton souhaité dans le span slot="button"</li>
            <li>passer le titre de la modale qui apparait au clic dans le span slot="modal_title"</li>
            <li>passer le texte de la modale qui apparait au clic dans le span slot="modal_text"</li>
        </p>

    </div>
</div>
<div class="flex">
    <div class="hover-ui">
        <Feeds darkMode={darkMode} checkpoints={checkpoints_list} />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Feeds</h2>
        <p> Le composant Feeds permet de créer des étapes de suivi, pour représenter l'avancée sur un sujet. 
            <br>
            Pour créer ses Feeds : 
            passer ses valeurs en array dans la variable checkpoints_list sous le format [ "text", "status", "date" ].
            <br>Les status disponsibles sont : sent, loading, closed, validated.
            <br>Chaque status est lié à une icône. 
        </p>
    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <UserCard darkMode={darkMode} persons={persons} />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>User card</h2>
        <p>Pour créer une carte utilisateur :
        Appelez le composant "UserCard /" en passant en props un tableau d'objet avec les paramètres "name: string, cover: string" et un darkMode avec les paramètre true/false
        </p>
    </div>
</div>

<div class="reviews">
    <div class="hover-ui">       
         <Reviews  darkMode={darkMode} reviewsInfo={reviewsInfo}></Reviews> 
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Reviews</h2>
        <p>Pour créer une carte d'avis:
            Appelez le composant "Reviews /" en passant en props un tableau d'objet avec les paramètres "name: string, title: string, description: string, stars: number(entre 0 et 5)"  et un darkMode avec les paramètre true/false
            </p>    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <Dropdown darkMode={darkMode} />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Dropdown</h2>
        <p>Le dropdown permet de créer une liste d'éléments cliquables.
            <br>
            Différentes props peuvents être spécifiées pour personnaliser le composant:
            <li>
                <strong>dropdownTitle</strong> le titre du dropdown
                <br>
                <p>Variable de type string</p>
            </li>
            <li>
                <strong>dropdownItems</strong> les éléments de la liste
                <br>
                <p>Tableau d'objets avec item</p>
            </li>
            <li>
                <strong>dropdownBtnBG</strong> couleur de bg du bouton
                <br>
                <p>Variable de type string avec code HEX</p>
            </li>
            <li>
                <strong>dropdownListBG</strong> Couleur de bg de la liste
                <br>
                <p>Variable de type string avec code HEX</p>
            </li>
            <li>
                <strong>EllipseColor</strong> la couleur de la puce de catégorie
                <br>
                <p>Variable de type string avec code HEX</p>
            </li>
            <li>
                <strong>EllipseImg</strong> image de la puce de catégorie
                <br>
                <p>Variable de type string avec lien de l'image</p>
            </li>
            <li>
                <strong>automaticClose</strong> le dropdown peut se fermer ou non après séléction
                <br>
                <p>Variable à true ou false</p>
            </li>
            <li>
                <strong>SelectedItemIsTitle</strong> l'élément séléctionné devient le titre du dropdown ou non
                <br>
                <p>Variable à true ou false</p>
            </li>

        </p>
    </div>
</div>

<div class="navbar">
    <div class="hover-ui">
        <Navbar darkMode={darkMode} />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Navbar</h2>
        <p>
            Ce composant est responsive et personnalisable avec ces props:
            <li>
                <strong>navbarItems</strong> les liens de la navbar
                <br>
                <p>Tableau d'objets avec item et link</p>
            </li>
            <li>
                <strong>navbarLogo</strong> le logo de la navbar
                <br>
                <p>Variable de type string avec lien de l'image</p>
            </li>
            <li>
                <strong>navbarBG</strong> couleur de bg de la navbar
                <br>
                <p>Variable de type string avec code HEX</p>
            </li>
        </p>
    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <Searchbar darkMode={darkMode}></Searchbar>
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Adress Searchbar</h2>
        <p>Ce component s'appuie sur l'API open data de la France. 
           Elle référence l'ensemble des adresses de France.
           Comme elle est gratuite, il n'y a pas d'API Key à lui passer.<br>
         </p>
    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <Steps darkMode={darkMode}/> 
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Steps</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<div class="flex">
    <div class="hover-ui">
        <InputNumber darkMode={darkMode}/>  
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>InputNumber</h2>
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Enim repudiandae sunt suscipit, fugiat hic eveniet perspiciatis eum officia quo? Dignissimos minima sunt iure magni sit repellendus officiis corrupti illo repellat.</p>
    </div>
</div>

<!-- <div class="flex"> -->
    <div >
        <Carousel 
        darkMode={darkMode}
        images={images} 
        imageWidth={250}
        imageSpacing={20}
    
    
    />
    </div>
    <div class={darkMode ?  'doc' : 'doc-dark'}>
        <h2>Carousel</h2>
        <p>Ce carousel vous permet d'afficher plusieurs photos et de les faires défiler vers la gauche ou la droite!!</p>
        <p>Passez simplement les liens des images que vous souhaitez afficher dans la variable array "images", vous pourrez ensuite modifier la width des images et l'écarts entre les images en modifiant les valeurs dans les props imageWidth et imageSpacing. </p>
    </div>
<!-- </div> -->

<!-- <Reviews darkMode={true} reviewsInfo={reviewsInfo}></Reviews>  -->
<br>
<br>
</div>

<div class="flex">

<div class="button-up" on:click={toggleMode}>
    <Button darkMode={darkMode}>
        {#if darkMode == true}
            Dark mode
        {:else}
            Light mode
        {/if}
    </Button>
</div>
<div class={darkMode ?  'doc' : 'doc-dark'}>
    <h2>Dark mode</h2>
    <p>Passez en props "darkMode" avec un boolean en props.</p>
</div>
</div>
<style>

    * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    /* font-family: 'Montserrat'; */
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
        gap: 50px;
        margin-bottom: 5em;
    }

    @media (max-width: 950px){
        .flex {
            flex-wrap: wrap;
        }
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
        margin-bottom: 5em;

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
.navbar {
  padding: 30px;
}
.navbar > .hover-ui {
  padding:50px 50px 50px 0;
}
.button-up {
    margin-bottom: 3em;
}
</style>


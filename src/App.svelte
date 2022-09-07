<script>

    import UserCard from "./UI/UserCard.svelte";
    import Dropdown from "./UI/Dropdown.svelte";
    import Feeds from "./UI/Feeds.svelte";
    import Toast from "./UI/Toast.svelte";
    import Searchbar from "./UI/Searchbar.svelte";
    import Button from "./UI/Button.svelte";
    import Reviews from "./UI/Reviews.svelte"
    

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
    }]
</script>

<h1>Nos composants</h1>
<h2>Toast</h2>
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

<h2>Feeds</h2>
<!-- 
    Pour créer ses Feeds : 
    donner ses valeurs dans la variable checkpoints_list sous le format [ "text", "status", "date" ].
    Les status disponsibles sont : sent, loading, closed, validated.
-->
<Feeds checkpoints={checkpoints_list} />


<h2>Dropdown</h2>
<Dropdown />

<h2>Adress Searchbar</h2>
<Searchbar></Searchbar>

<div class="flex">
    <UserCard darkMode={true} persons={persons} />
    <UserCard darkMode={false} persons={persons} />
</div>
<Reviews darkMode={false} reviewsInfo={reviewsInfo}></Reviews> 
<Reviews darkMode={true} reviewsInfo={reviewsInfo}></Reviews> 
<Button darkMode={false} />
<Button darkMode={true} />


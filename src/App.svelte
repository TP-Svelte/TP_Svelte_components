<script>
  import Feeds from "./UI/Feeds.svelte";
  import Toast from "./UI/Toast.svelte";
  
  let checkpoints_list = [
      [ "Dossier envoyé", "sent", "2 sept" ],
      [ "Dossier en cours de traitement", "loading", "2 sept" ],
      [ "Dossier refusé", "closed", "5 sept" ],
      [ "Dossier en cours de réévaluation", "loading", "6 sept"],
      [ "Dossier accepté", "validated", "15 sept" ]    
    ];
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
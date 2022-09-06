<script>
  import Feeds from "./UI/Feeds.svelte";
  
  let checkpoints_list = [
      [ "Dossier envoyé", "sent", "2 sept" ],
      [ "Dossier en cours de traitement", "loading", "2 sept" ],
      [ "Dossier refusé", "closed", "5 sept" ],
      [ "Dossier en cours de réévaluation", "loading", "6 sept"],
      [ "Dossier accepté", "validated", "15 sept" ]    
    ];
</script>

<h1>Nos composants</h1>
<h2>Feeds</h2>
<Feeds checkpoints={checkpoints_list} />
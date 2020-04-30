---
description: Le lecteur TVSDK distribue des événements pour afficher l’état de chargement personnalisé de la publicité ou pour ignorer une publicité dont le chargement prend trop de temps ou comporte des erreurs. Ces événements sont définis dans événements.CustomAdEvents.
seo-description: Le lecteur TVSDK distribue des événements pour afficher l’état de chargement personnalisé de la publicité ou pour ignorer une publicité dont le chargement prend trop de temps ou comporte des erreurs. Ces événements sont définis dans événements.CustomAdEvents.
seo-title: événements publicitaires personnalisés
title: événements publicitaires personnalisés
uuid: 78e2ccf4-5943-4c60-84be-623182d9a300
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# événements publicitaires personnalisés{#custom-ad-events}

Le lecteur TVSDK distribue des événements pour afficher l’état de chargement personnalisé de la publicité ou pour ignorer une publicité dont le chargement prend trop de temps ou comporte des erreurs. Ces événements sont définis dans événements.CustomAdEvents.

<table id="table_718700E0F0B042F882ED131F79E01D4E"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Événement </th> 
   <th colname="col2" class="entry"> Définition </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdClickThru </span> </td> 
   <td colname="col2"> Nombre de fois où le lecteur a cliqué sur une publicité personnalisée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdError </span> </td> 
   <td colname="col2"> Une erreur s'est produite avec l'annonce personnalisée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoaded </span> </td> 
   <td colname="col2"> La publicité personnalisée a été chargée.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoading </span> </td> 
   <td colname="col2"> La publicité personnalisée est en cours de chargement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPaused </span> </td> 
   <td colname="col2"> La publicité personnalisée est en pause. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdResumed </span> </td> 
   <td colname="col2"> La lecture de la publicité personnalisée s’est poursuivie après une pause. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPlaying </span> </td> 
   <td colname="col2"> La publicité personnalisée est en cours de lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdProgress </span> </td> 
   <td colname="col2"> <p>Le lecteur d’annonce personnalisé informe le lecteur TVSDK de la progression de l’annonce personnalisée. &amp;nbsp; </p> <p>L’heure <span class="codeph"> actuelle </span> et l’heure <span class="codeph"> totale </span> de la publicité sont transmises avec ce événement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStarted </td> 
   <td colname="col2"> La lecture de la publicité personnalisée a commencé et s’affiche au lecteur.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStpped </td> 
   <td colname="col2"> La lecture de la publicité personnalisée est terminée. </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_027774C2A47C453BA9DED61C6F8567C3"></a>-->


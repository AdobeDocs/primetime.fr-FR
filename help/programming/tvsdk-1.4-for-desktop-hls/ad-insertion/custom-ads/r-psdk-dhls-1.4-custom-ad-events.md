---
description: Le lecteur TVSDK distribue des événements pour afficher l’état de chargement personnalisé de la publicité ou pour ignorer une publicité dont le chargement prend trop de temps ou comporte des erreurs. Ces événements sont définis dans événements.CustomAdEvents.
title: Événements publicitaires personnalisés
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Événements publicitaires personnalisés{#custom-ad-events}

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
   <td colname="col1"> <span class="codeph"> AdClickThru  </span> </td> 
   <td colname="col2"> Nombre de fois où le lecteur a cliqué sur une publicité personnalisée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdError  </span> </td> 
   <td colname="col2"> Une erreur s'est produite avec l'annonce personnalisée. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoaded  </span> </td> 
   <td colname="col2"> La publicité personnalisée a été chargée.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoading  </span> </td> 
   <td colname="col2"> La publicité personnalisée est en cours de chargement. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPaused  </span> </td> 
   <td colname="col2"> La publicité personnalisée est en pause. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdResumed  </span> </td> 
   <td colname="col2"> La lecture de la publicité personnalisée s’est poursuivie après une pause. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPlaying  </span> </td> 
   <td colname="col2"> La publicité personnalisée est en cours de lecture. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdProgress  </span> </td> 
   <td colname="col2"> <p>Le lecteur d’annonce personnalisé informe le lecteur TVSDK de la progression de l’annonce personnalisée. &amp;nbsp; </p> <p>Les <span class="codeph"> currentTime </span> et <span class="codeph"> totalTime </span> de la publicité sont transmis avec ce événement. </p> </td> 
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


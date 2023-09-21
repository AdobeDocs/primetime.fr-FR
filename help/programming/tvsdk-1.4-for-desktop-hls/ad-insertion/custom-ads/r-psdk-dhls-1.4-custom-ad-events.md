---
description: Le lecteur TVSDK distribue des événements pour afficher l’état de chargement de publicité personnalisé ou pour ignorer une publicité dont le chargement prend trop de temps ou qui comporte des erreurs. Ces événements sont définis dans events.CustomAdEvents.
title: Événements publicitaires personnalisés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Événements publicitaires personnalisés{#custom-ad-events}

Le lecteur TVSDK distribue des événements pour afficher l’état de chargement de publicité personnalisé ou pour ignorer une publicité dont le chargement prend trop de temps ou qui comporte des erreurs. Ces événements sont définis dans events.CustomAdEvents.

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
   <td colname="col2"> Une erreur s’est produite avec la publicité personnalisée. </td> 
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
   <td colname="col2"> La publicité personnalisée a été suspendue. </td> 
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
   <td colname="col2"> <p>Le lecteur de publicités personnalisé informe le lecteur TVSDK de la progression de la publicité personnalisée. &amp;nbsp; </p> <p>La variable <span class="codeph"> currentTime </span> et <span class="codeph"> totalTime </span> de la publicité sont transmises avec cet événement. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStarted </td> 
   <td colname="col2"> La lecture de la publicité personnalisée a commencé et s’affiche pour la visionneuse.  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStoppé </td> 
   <td colname="col2"> La lecture de la publicité personnalisée est terminée. </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_027774C2A47C453BA9DED61C6F8567C3"></a>-->

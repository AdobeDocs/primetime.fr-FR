---
description: Ces classes fournissent des informations sur la chronologie d’un média particulier, y compris le placement des publicités.
title: Classes de journal
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Classes de journal{#timeline-classes}

Ces classes fournissent des informations sur la chronologie d’un média particulier, y compris le placement des publicités.

Package : [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Nom </th> 
   <th colname="2" class="entry"> <p>Description </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ContentTracker </a> </span> </td> 
   <td colname="2"> Interface qui définit le protocole que vous devez implémenter si vous souhaitez créer un module de suivi de contenu conçu pour s’intégrer à la bibliothèque TVSDK. <p>Cette interface requiert que vous définissiez la manière dont les événements de progression sont signalés au système de suivi distant. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> Opportunité </a> </span> </td> 
   <td colname="2"> Classe de base pour toutes les classes d’opportunité. Une classe d'opportunité représente un point "intéressant" sur la chronologie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> Placement </a> </span> </td> 
   <td colname="2"> Classe qui encapsule les informations relatives au placement dans la chronologie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> PlacementMode </a> </span> </td> 
   <td colname="2"> Énumération des modes de placement, par exemple pour insérer ou remplacer du contenu. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> PlacementType </a> </span> </td> 
   <td colname="2"> Énumération des types d’emplacement qui indiquent où l’emplacement est effectué dans la chronologie ; par exemple, PRE_ROLL. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> Réservation </a> </span> </td> 
   <td colname="2"> Une réservation est utilisée pour limiter ou empêcher tout traitement ultérieur d’une période donnée dans la chronologie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> Chronologie </a> </span> </td> 
   <td colname="2"> Interface qui fournit un itérateur pour le traitement des marqueurs de chronologie. Représente la chronologie du contenu, y compris les coupures publicitaires. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem </a> </span> </td> 
   <td colname="2"> Classe. Représentation générique non modifiable d’un élément de chronologie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker </a> </span> </td> 
   <td colname="2"> Classe qui représente un marqueur sur la chronologie. Ceci marque une région d’intérêt sur la chronologie réelle. Actuellement, les zones d’intérêt sont les publicités, que vous pouvez par exemple marquer avec une couleur différente sur l’interface utilisateur de la barre de défilement. Chaque marqueur est défini par une position et une durée (chacune exprimée en millisecondes). </td> 
  </tr> 
 </tbody> 
</table>

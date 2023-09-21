---
description: Ces classes fournissent des informations sur la chronologie d’un média particulier, y compris le placement des publicités.
title: Classes de journal
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Classes de journal{#timeline-classes}

Ces classes fournissent des informations sur la chronologie d’un média particulier, y compris le placement des publicités.

Package : [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Nom </th> 
   <th colname="2" class="entry"> <p>Description </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/PlacementOpportunity.html" format="html" scope="external"> PlacementOpportunity</a></span> </td> 
   <td colname="2"> Une classe d’opportunité représente un point ciblé sur la chronologie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> Chronologie</a> </td> 
   <td colname="2"> Interface qui fournit un itérateur pour le traitement des marqueurs de chronologie. Représente la chronologie du contenu, y compris les coupures publicitaires. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem</a> </span> </td> 
   <td colname="2"> Classe. Représentation générique non modifiable d’un élément de chronologie. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker</a> </span> </td> 
   <td colname="2"> Interface qui représente un marqueur sur la chronologie. Ceci marque une région d’intérêt sur la chronologie réelle. Actuellement, les zones d’intérêt sont les publicités, que vous pouvez par exemple marquer avec une couleur différente sur l’interface utilisateur de la barre de défilement. Chaque marqueur est défini par une position et une durée (chacune exprimée en millisecondes). </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/timeline/TimelineOperation.html" format="html" scope="external"> TimelineOperation</a> </td> 
   <td colname="2"> Classe de base pour toutes les opérations qui affectent la chronologie. </td> 
  </tr> 
 </tbody> 
</table>

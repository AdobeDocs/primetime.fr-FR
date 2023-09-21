---
description: Le système de notification TVSDK génère divers avis d’erreur, d’avertissement et d’information fournissant des métadonnées de diagnostic.
title: Codes de notification
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Présentation {#notification-codes-overview}

Le système de notification TVSDK génère divers avis d’erreur, d’avertissement et d’information fournissant des métadonnées de diagnostic.

Les objets de notification fournissent des informations relatives à l’état du lecteur. TVSDK fournit une liste d’objets de notification triés chronologiquement. Chaque notification contient les métadonnées suivantes :

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Élément </th> 
   <th colname="2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> <p>Type de notification. </p> <p>Selon la plateforme, cette propriété est un type énuméré avec les valeurs possibles INFO, WARN et ERROR. Il s’agit du regroupement de niveau supérieur pour les notifications. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> code</span> </td> 
   <td colname="2"> <p>Les représentations numériques suivantes sont affectées aux notifications : 
     <ul id="ul_A86BF89D6B3B410E81FAD718D3C4A9F0"> 
      <li id="li_8180972D704C40098723734DD4B45643">Événements de notification d’erreur, de 100000 à 199999 </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">Événements de notification d’avertissement, de 200000 à 299999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">Événements de notification d’informations, de 300000 à 399999 </li> 
     </ul> </p> <p>Chaque plage de niveau supérieur (erreurs, par exemple) est divisée en sous-plages, telles que 101000 à 101999, représentant les erreurs de lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Chaîne contenant une description lisible de l’événement de notification, telle que <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metadata</span> </td> 
   <td colname="2"> <p>Paires clé/valeur contenant des informations supplémentaires sur la notification. </p> <p>Par exemple, une clé nommée <span class="codeph"> URL</span> fournit une valeur qui est une URL liée à la notification, telle qu’une URL non valide qui a provoqué une erreur. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>Une référence à une autre <span class="codeph"> MediaPlayerNotification</span> qui ont directement affecté cette notification. </p> <p>Par exemple, une notification d’échec de l’insertion publicitaire correspond directement à un conflit d’insertion de ligne temporelle. Toutes les notifications ne fournissent pas de notification interne. </p> </td> 
  </tr> 
 </tbody> 
</table>

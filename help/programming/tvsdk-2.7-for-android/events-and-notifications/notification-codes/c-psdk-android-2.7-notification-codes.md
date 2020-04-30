---
description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-title: Codes de notification
title: Codes de notification
uuid: 24476204-5c35-4ff9-810d-77698ea18b53
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#notification-codes-overview}

Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.

Les objets de notification fournissent des informations relatives à l’état du lecteur. TVSDK fournit une liste chronologiquement triée des objets de notification. Chaque notification contient les métadonnées suivantes :

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Elément </th> 
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
      <li id="li_8180972D704C40098723734DD4B45643">événements de notification d'erreur, de 100000 à 199999 </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">événements de notification d'avertissement, de 20000 à 29999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">événements de notification des informations, de 300000 à 399999 </li> 
     </ul> </p> <p>Chaque plage de niveau supérieur, telle que les erreurs, est divisée en sous-plages, par exemple de 101 000 à 101 999, ce qui représente des erreurs de lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Chaîne contenant une description lisible du événement de notification, telle que <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metadata</span> </td> 
   <td colname="2"> <p>paires clé/valeur qui contient des informations pertinentes supplémentaires sur la notification. </p> <p>Par exemple, une clé nommée <span class="codeph"> URL</span> fournit une valeur qui est une URL liée à la notification, telle qu’une URL non valide qui a provoqué une erreur. </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>Référence à un autre objet <span class="codeph"> MediaPlayerNotification</span> qui a directement affecté cette notification. </p> <p>Par exemple, une notification d’échec d’insertion publicitaire peut correspondre directement à un conflit d’insertion chronologique. Toutes les notifications ne fournissent pas de notification interne. </p> </td> 
  </tr> 
 </tbody> 
</table>


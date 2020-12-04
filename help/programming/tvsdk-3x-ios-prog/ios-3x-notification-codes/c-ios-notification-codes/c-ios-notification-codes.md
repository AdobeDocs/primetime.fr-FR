---
description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-title: Système de notification TVSDK
title: Système de notification TVSDK
uuid: cace3b4d-ac2b-4fb2-854e-ce6db17544f5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# Système de notification TVSDK {#tvsdk-notification-system}

Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.

Les objets de notification fournissent des informations relatives à l’état du lecteur. TVSDK fournit une liste chronologiquement triée des objets de notification et chaque notification contient les métadonnées suivantes :

<table frame="all" colsep="1" rowsep="1" id="table_DBA8CACF02DB4AF2B053E560850B49CE"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Elément </th> 
   <th colname="2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> Type de notification. Selon la plateforme, cette propriété fait référence à un type énuméré avec des valeurs possibles d’INFO, WARN ou ERROR. Il s’agit du regroupement de niveau supérieur pour les notifications. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> code</span> </td> 
   <td colname="2">Représentation numérique affectée à la notification. 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">Événements de notification d'erreur, de 100000 à 199999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">Événements de notification d'avertissement, de 20000 à 29999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">Événements de notification des informations, de 300000 à 399999 </li> 
    </ul> <p>Chaque plage de niveau supérieur, telle que les erreurs, est divisée en sous-plages, par exemple de 101 000 à 101 999, ce qui représente des erreurs de lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Chaîne contenant une description lisible du code, telle que <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metadata</span> </td> 
   <td colname="2">paires clé/valeur qui contient des informations pertinentes supplémentaires sur la notification. Par exemple, une clé nommée <span class="codeph"> URL</span> sera associée à une valeur qui est une URL liée à la notification, telle qu’une URL non valide qui a provoqué une erreur. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2">Référence à un autre objet <span class="codeph"> PTNotification</span> qui a directement affecté cette notification. Par exemple, une notification d’échec d’insertion publicitaire peut correspondre directement à un conflit d’insertion chronologique. Toutes les notifications ne fournissent pas de notification interne. </td> 
  </tr> 
 </tbody> 
</table>
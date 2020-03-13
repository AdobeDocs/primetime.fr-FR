---
description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-description: Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.
seo-title: Codes de notification
title: Codes de notification
uuid: edbce737-28fd-4309-be5a-2e33fcc156b6
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Codes de notification{#notification-codes}

Le système de notification TVSDK produit divers avis d’erreur, d’avertissement et d’information qui fournissent des métadonnées de diagnostic.

Les objets de notification fournissent des informations relatives à l’état du lecteur. TVSDK fournit un trié chronologiquement des objets de notification et chaque notification contient les métadonnées suivantes :

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
   <td colname="2">Type de notification. Selon la plateforme, cette propriété fait référence à un type énuméré avec des valeurs possibles d’ <span class="codeph"> INFO</span>, <span class="codeph"> WARN</span>ou <span class="codeph"> ERROR</span>. Il s’agit du regroupement de niveau supérieur pour les notifications. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> code</span> </td> 
   <td colname="2">Représentation numérique affectée à la notification : 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">de notification d’erreur, de 100000 à 19999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A"> de notification d'avertissement, de 200000 à 29999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">de notification des informations, de 300000 à 399999 </li> 
    </ul> <p>Chaque plage de niveau supérieur, par exemple les erreurs, est divisée en sous-plages, par exemple 101000 à 101999 représentant les erreurs de lecture. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2">Chaîne contenant une description du code lisible par un utilisateur, telle que <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> métadonnées</span> </td> 
   <td colname="2">paires clé/valeur qui contiennent des informations pertinentes supplémentaires sur la notification. Par exemple, une clé nommée <span class="codeph"> URL</span> serait associée à une valeur qui est une URL liée à la notification, telle qu’une URL non valide qui a provoqué une erreur. </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2">Référence à un autre objet <span class="codeph"> MediaPlayerNotification</span> qui affectait directement cette notification. Par exemple, une notification d’échec d’insertion d’une annonce publicitaire peut correspondre directement à un conflit d’insertion dans le temps. Toutes les notifications ne fournissent pas de notification interne. </td> 
  </tr> 
 </tbody> 
</table>


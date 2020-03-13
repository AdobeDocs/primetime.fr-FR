---
description: Vous pouvez configurer un contrôle d’interface utilisateur pour le volume sonore.
seo-description: Vous pouvez configurer un contrôle d’interface utilisateur pour le volume sonore.
seo-title: Contrôler le volume
title: Contrôler le volume
uuid: c51e99b6-efd1-414e-9ef7-77bd53e0d6c0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Contrôler le volume{#provide-volume-control}

Vous pouvez configurer un contrôle d’interface utilisateur pour le volume sonore.

1. Attendez que l’instance MediaPlayer soit dans un état valide pour cette commande.

   Tout état sauf RELEASED est valide.
1. Appelez la méthode d&#39;ensemble de volumes sur l&#39; `MediaPlayer` instance pour définir le volume audio.

   ```
   public function set volume(value:Number):void
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximal, où 0 est silencieux et 1 est le volume maximal.

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> Si le volume spécifié est </th> 
      <th colname="col2" class="entry"> Le volume résultant est </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> Moins de 0 </td> 
      <td colname="col2"> 0 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Entre 0 et 1 </td> 
      <td colname="col2"> Le volume spécifié </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Supérieur à 1 </td> 
      <td colname="col2"> Valeur divisée par 100 et définie sur l’une des valeurs suivantes : 
      <ul id="ul_8C2282F0EDC44A408820F5768709214F"> 
      <li id="li_B00BC6F4812D4000891358F762C8E492">Le résultat est compris entre 0 et 1 </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">1 si le résultat est supérieur à 1 </li> 
      </ul> <p>Conseil :  Cette logique gère les valeurs fournies par les clients en fonction des versions antérieures des <span class="codeph">expressions/primetime-sdk-name</span>, où les valeurs de volume variaient de 0 à 100. </p> </td> 
   </tr> 
   </tbody> 
   </table>

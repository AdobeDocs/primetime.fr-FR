---
description: Vous pouvez configurer une commande de l’interface utilisateur pour le volume sonore.
title: Contrôle du volume
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Contrôle du volume{#provide-volume-control}

Vous pouvez configurer une commande de l’interface utilisateur pour le volume sonore.

1. Attendez que l’instance MediaPlayer soit dans un état valide pour cette commande.

   Tout état sauf sauf RELEASED est valide.
1. Appelez la méthode volume set sur le `MediaPlayer` pour définir le volume audio.

   ```
   public function set volume(value:Number):void
   ```

   La valeur du volume représente le volume demandé exprimé en proportion du volume maximum, où 0 est silencieux et 1 est le volume maximum.

   <table id="table_144A2B1260374FBE8D976194F602DDC7"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> Si le volume spécifié est </th> 
      <th colname="col2" class="entry"> Le volume obtenu est le suivant : </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> Moins de 0 </td> 
      <td colname="col2"> 0 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Entre 0 et 1 </td> 
      <td colname="col2"> Volume spécifié </td> 
   </tr> 
   <tr> 
      <td colname="col1"> Supérieur à 1 </td> 
      <td colname="col2"> La valeur divisée par 100 et définie sur l’une des valeurs suivantes : 
      <ul id="ul_8C2282F0EDC44A408820F5768709214F"> 
      <li id="li_B00BC6F4812D4000891358F762C8E492">Le résultat est compris entre 0 et 1 </li> 
      <li id="li_03B7F30662554F299320040CAC2DEB7A">1 si le résultat est supérieur à 1 </li> 
      </ul> <p>Conseil : Cette logique gère les valeurs fournies par les clients en fonction des versions antérieures de la variable 
      <span class="codeph">expressions/primetime-sdk-name</span>, où les valeurs du volume sont comprises entre 0 et 100. </p> </td> 
   </tr> 
   </tbody> 
   </table>

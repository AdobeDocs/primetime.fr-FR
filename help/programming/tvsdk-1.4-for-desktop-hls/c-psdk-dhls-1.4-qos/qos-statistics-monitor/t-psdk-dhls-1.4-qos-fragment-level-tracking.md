---
description: Vous pouvez lire les informations de qualité de service (QoS) sur les ressources téléchargées, telles que les fragments et les pistes, à partir de la classe LoadInformation.
seo-description: Vous pouvez lire les informations de qualité de service (QoS) sur les ressources téléchargées, telles que les fragments et les pistes, à partir de la classe LoadInformation.
seo-title: Suivi au niveau du fragment à l’aide des informations de chargement
title: Suivi au niveau du fragment à l’aide des informations de chargement
uuid: 41fb2b90-3531-4cc5-bf9b-01ccae04d2fd
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Suivi au niveau du fragment à l’aide des informations de chargement{#track-at-the-fragment-level-using-load-information}

Vous pouvez lire les informations de qualité de service (QoS) sur les ressources téléchargées, telles que les fragments et les pistes, à partir de la classe LoadInformation.

1. Mettez en oeuvre le `onLoadInformationAvailable` module d’écoute de de rappel.

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. Enregistrez l’écouteur de , que TVSDK appelle chaque fois qu’un fragment est téléchargé.

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. Lisez les données présentant un intérêt depuis le `LoadInformation` qui est transmis au rappel.

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> Propriété </th> 
      <th colname="col1" class="entry"> Type </th> 
      <th colname="col2" class="entry"> Description </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration </span> </td> 
      <td colname="col1"> <p>Nombre </p> </td> 
      <td colname="col2"> <p>Durée du téléchargement en millisecondes. </p> <p>TVSDK ne fait pas la distinction entre le temps nécessaire au client pour se connecter au serveur et le temps nécessaire pour télécharger le fragment complet. Par exemple, si le téléchargement d’un segment de 10 Mo prend 8 secondes, TVSDK fournit ces informations, mais ne vous indique pas qu’il a fallu 4 secondes avant le premier octet et 4 secondes pour télécharger l’intégralité du fragment. </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <p>Nombre </p> </td> 
      <td colname="col2"> Durée du média des fragments téléchargés en millisecondes. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> taille </span> </td> 
      <td colname="col1"> <p>Nombre </p> </td> 
      <td colname="col2"> Taille de la ressource téléchargée en octets. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> Index de la piste correspondante, s'il est connu; sinon, 0. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> Le nom de la piste correspondante, s'il est connu; sinon, null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> Le type de la piste correspondante, s'il est connu; sinon, null. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> Ce que TVSDK a téléchargé. L’un des éléments suivants : 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST - Liste de lecture/manifeste </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT - Un fragment </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK : fragment associé à une piste spécifique </li> 
      </ul> Il peut parfois être impossible de détecter le type de ressource. Si cela se produit, le fichier est renvoyé. </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <p>Chaîne </p> </td> 
      <td colname="col2"> URL pointant vers la ressource téléchargée. </td> 
   </tr> 
   </tbody> 
   </table>

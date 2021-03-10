---
description: Lorsque le lecteur de médias bascule son profil actuel sur un nouveau profil, vous pouvez récupérer des informations sur le commutateur, y compris le moment où il a basculé, les informations de largeur et de hauteur, ou les raisons pour lesquelles un débit binaire différent a été utilisé.
title: Obtenir des informations sur le commutateur de profil
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Obtenir des informations sur le commutateur de profil{#get-information-about-profile-switch}

Lorsque le lecteur de médias bascule son profil actuel sur un nouveau profil, vous pouvez récupérer des informations sur le commutateur, y compris le moment où il a basculé, les informations de largeur et de hauteur, ou les raisons pour lesquelles un débit binaire différent a été utilisé.

1. Prêtez attention au événement `AdobePSDK.PSDKEventType.PROFILE_CHANGED`.

   Le lecteur multimédia du navigateur TVSDK distribue ce événement lorsque son algorithme de commutation de débit binaire adaptatif passe à un autre profil en raison des conditions réseau ou de l’ordinateur. (Lorsque le débit ou la période change.)
1. Lorsque le événement se produit, vérifiez les propriétés suivantes pour obtenir des informations sur le commutateur :

   * `profile`: Identifiant du nouveau profil utilisé.
   * `time`: Moment du flux auquel le commutateur s&#39;est produit.
   * `description`: Description textuelle de la raison d’un changement de débit binaire, sous la forme d’une chaîne de paires clé/valeur séparées par des points-virgules. Inclut un maximum de `Reason` et un `Bitrate`. Si les informations ne sont pas disponibles ou si le débit binaire n’a pas changé, cette chaîne est vide.

   <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Nom de la clé </th> 
      <th colname="col2" class="entry"> Valeurs possibles </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Raison  </span> </td> 
      <td colname="col2"> 
        <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
        <li id="li_E374B029E1AF40689D70A9D30E057C5B">Adaptation du réseau </li> 
        <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">Recherche </li> 
        <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">Profil non pris en charge </li> 
        <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">Basculement </li> 
        </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Débit  </span> </td> 
      <td colname="col2"> 
        <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
        <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> up  </span>: Augmentation du débit binaire </li> 
        <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> down  </span>: Le débit binaire a diminué </li> 
        </ul> </td> 
      </tr> 
    </tbody> 
    </table>

   Voici quelques exemples de chaînes `description` renvoyées :

   ```
   "Bitrate::=up;Reason::=Network Adaptation;" 
   
   "Bitrate::=down;Reason::=Failover;"
   ```

   * `width`: Entier indiquant la largeur en pixels.
   * `height`: Entier indiquant la hauteur en pixels.

   >[!NOTE]
   >
   >Les données de largeur et de hauteur ne sont disponibles que lorsqu’elles sont incluses dans la balise `RESOLUTION` du manifeste M3U8. Si les informations ne sont pas incluses dans le M3U8, les propriétés de largeur et de hauteur sont définies sur 0, car elles ne font pas partie des informations du profil.

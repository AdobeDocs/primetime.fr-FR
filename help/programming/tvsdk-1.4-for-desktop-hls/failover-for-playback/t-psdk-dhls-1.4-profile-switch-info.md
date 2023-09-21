---
description: Lorsque le lecteur multimédia bascule son profil actuel vers un nouveau profil, vous pouvez récupérer des informations sur le commutateur, y compris le moment où il a été activé, les informations de largeur et de hauteur, ou la raison pour laquelle un débit différent a été utilisé.
title: Obtenir des informations sur le sélecteur de profil
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Obtenir des informations sur le sélecteur de profil{#get-information-about-profile-switch}

Lorsque le lecteur multimédia bascule son profil actuel vers un nouveau profil, vous pouvez récupérer des informations sur le commutateur, y compris le moment où il a été activé, les informations de largeur et de hauteur, ou la raison pour laquelle un débit différent a été utilisé.

1. Écoute de la `ProfileEvent.PROFILE_CHANGED` .

   Le lecteur multimédia TVSDK distribue cet événement lorsque son algorithme de changement de débit adaptatif passe à un autre profil en raison des conditions du réseau ou de la machine. (Lorsque le débit ou la période change.)
1. Lorsque l’événement se produit, vérifiez les propriétés suivantes pour plus d’informations sur le commutateur :

   * `profile`: identifiant du nouveau profil utilisé.
   * `time`: moment du flux auquel le commutateur s’est produit.
   * `description`: description textuelle de la raison d’un changement de débit, sous la forme d’une chaîne de paires clé/valeur séparées par des points-virgules. Inclut un maximum de 1 `Reason` et un `Bitrate`. Si les informations ne sont pas disponibles ou que le débit n’a pas changé, cette chaîne est vide.

     <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
       <thead> 
         <tr> 
         <th colname="col1" class="entry"> Nom de la clé </th> 
         <th colname="col2" class="entry"> Valeurs possibles </th> 
         </tr> 
       </thead>
       <tbody> 
         <tr> 
         <td colname="col1"> <span class="codeph"> Motif </span> </td> 
         <td colname="col2"> 
          <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
          <li id="li_E374B029E1AF40689D70A9D30E057C5B">Adaptation réseau </li> 
          <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">Recherche </li> 
          <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B">Profil non pris en charge </li> 
          <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">Basculement </li> 
          </ul> </td> 
         </tr> 
         <tr> 
         <td colname="col1"> <span class="codeph"> Débit binaire </span> </td> 
         <td colname="col2"> 
          <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
          <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> up </span>: le débit a augmenté </li> 
          <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> down </span>: le débit a baissé. </li> 
          </ul> </td> 
         </tr> 
       </tbody> 
       </table>

     Voici quelques exemples de renvoi `description` chaînes :

     ```
     "Bitrate::=up;Reason::=Network Adaptation;" 
     
     "Bitrate::=down;Reason::=Failover;"
     ```

   * `width`: entier indiquant la largeur en pixels.
   * `height`: nombre entier indiquant la hauteur en pixels.

     >[!NOTE]
     >
     >Les données de largeur et de hauteur ne sont disponibles que lorsqu’elles sont incluses dans la variable `RESOLUTION` dans le manifeste M3U8. Si les informations ne sont pas incluses dans le M3U8, les propriétés de largeur et de hauteur sont définies sur 0, car elles ne font pas partie des informations de profil.

<!--<a id="example_A713D420AE2E4E3CB7B78C6BC732BE90"></a>-->

Par exemple :

```
_player.addEventListener(ProfileEvent.PROFILE_CHANGED, onProfileChange); 
private function onProfileChange(event:ProfileEvent):void { 
    _logger.info("#onProfileChange Current profile/bitrate has changed.  
      {0} for reason {1} of resolution [ {2} , {3} ]",  
      event.profile, event.description, event.width, event.height); 
}
```

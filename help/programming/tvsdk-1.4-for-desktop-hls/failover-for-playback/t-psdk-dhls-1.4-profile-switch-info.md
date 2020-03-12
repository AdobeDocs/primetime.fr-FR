---
description: Lorsque le lecteur de médias bascule son  actuel vers un nouveau  de, vous pouvez récupérer des informations sur le commutateur, y compris lorsqu’il est activé, des informations sur la largeur et la hauteur ou la raison pour laquelle un débit binaire différent a été utilisé.
seo-description: Lorsque le lecteur de médias bascule son  actuel vers un nouveau  de, vous pouvez récupérer des informations sur le commutateur, y compris lorsqu’il est activé, des informations sur la largeur et la hauteur ou la raison pour laquelle un débit binaire différent a été utilisé.
seo-title: 'Obtenir des informations sur le commutateur '
title: 'Obtenir des informations sur le commutateur '
uuid: e26ad9fb-6c54-450e-ab62-784d9033d214
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Obtenir des informations sur le commutateur{#get-information-about-profile-switch}

Lorsque le lecteur de médias bascule son  actuel vers un nouveau  de, vous pouvez récupérer des informations sur le commutateur, y compris lorsqu’il est activé, des informations sur la largeur et la hauteur ou la raison pour laquelle un débit binaire différent a été utilisé.

1. Écoute le `ProfileEvent.PROFILE_CHANGED` .

   Le lecteur multimédia TVSDK distribue ce lorsque son algorithme de commutation de débit binaire adaptatif bascule vers un autre  en raison des conditions réseau ou machine. (Lorsque le débit ou la période change.)
1. Lorsque le se produit, vérifiez les propriétés suivantes pour plus d’informations sur le commutateur :

   * `profile`: Identifiant du nouveau utilisé.
   * `time`: Moment du flux auquel le commutateur s’est produit.
   * `description`: Description textuelle de la raison d’un changement de débit binaire, sous la forme d’une chaîne de paires clé/valeur séparées par des points-virgules. Inclut un maximum de un `Reason` et un `Bitrate`. Si les informations ne sont pas disponibles ou si le débit n’a pas changé, cette chaîne est vide.
   <table id="table_E400FD9C57FF40CBAC14AF6847CD8301"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> Nom de la clé </th> 
      <th colname="col2" class="entry"> Valeurs possibles </th> 
      </tr> 
    </thead>
    <tbody> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Raison </span> </td> 
      <td colname="col2"> 
       <ul id="ul_37DDE3F297634ED6B47DF5D73F969369"> 
       <li id="li_E374B029E1AF40689D70A9D30E057C5B">Adaptation du réseau </li> 
       <li id="li_753862EEF1C9474EA8E20C89F5EF5D8D">Rechercher </li> 
       <li id="li_EC14923F92CF4D11A47928A8D2DE6D8B"> non pris en charge </li> 
       <li id="li_695AB4A89C9D4833AF6D8B6424FC912B">Basculement </li> 
       </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> Débit </span> </td> 
      <td colname="col2"> 
       <ul id="ul_1B49BD90A91147359712E1AFD8877E23"> 
       <li id="li_1C8E593C65D34742B14A8D0EAD43E0A9"> <span class="codeph"> up </span>: Le débit binaire a augmenté </li> 
       <li id="li_B1A00E3985A849B6855E15CF70D79BB8"> <span class="codeph"> vers le bas </span>: Le débit binaire a diminué </li> 
       </ul> </td> 
      </tr> 
    </tbody>
</table>

    Voici quelques exemples de chaînes &quot;description&quot; renvoyées:
    
    &quot;
    &quot;Bitrate::=up;Reason:=Network Adaptation;&quot;
    
    &quot;Bitrate::=down;Reason:=Failover;&quot;
    &quot;
    
    * `width`: Entier indiquant la largeur en pixels.
    * &quot;hauteur&quot;: Entier indiquant la hauteur en pixels.
    
    >[!NOTE]
    >
    >Les données de largeur et de hauteur ne sont disponibles que lorsqu&#39;elles sont incluses dans la balise &quot;RESOLUTION&quot; du manifeste M3U8. Si les informations ne sont pas incluses dans le M3U8, les propriétés de largeur et de hauteur sont définies sur 0, car elles ne font pas partie des informations  du.

<!--<a id="example_A713D420AE2E4E3CB7B78C6BC732BE90"></a>-->

Par exemple :

```
_player.addEventListener(ProfileEvent.PROFILE_CHANGED, onProfileChange); 
private function onProfileChange(event:ProfileEvent):void { 
    _logger.info("#onProfileChange Current profile/bitrate has changed.  
      {0} for reason {1} of resolution [ {2} , {3} ]",  
      event.profile, event.description, event.width, event.height); 
}
```

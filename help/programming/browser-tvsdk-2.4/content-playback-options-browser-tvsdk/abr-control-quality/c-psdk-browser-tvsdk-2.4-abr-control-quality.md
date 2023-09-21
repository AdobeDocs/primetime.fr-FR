---
description: Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. Le TVSDK du navigateur peut sélectionner le niveau de qualité pour chaque rafale en fonction de la bande passante disponible.
title: Taux de bits adaptatifs (ABR) pour la qualité vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# Présentation {#adaptive-bit-rates-abr-for-video-quality-overview}

Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. Le TVSDK du navigateur peut sélectionner le niveau de qualité pour chaque rafale en fonction de la bande passante disponible.

Le TVSDK du navigateur surveille constamment le débit afin de s’assurer que le contenu est lu à un débit optimal pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de changement de débit adaptatif (ABR) et les débits initiaux, minimaux et maximales pour un flux à débit multiple (MBR). Le TVSDK du navigateur passe automatiquement au débit qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2">Débit de lecture souhaité (en bits par seconde) pour le premier segment. Au démarrage de la lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, le TVSDK du navigateur sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, le Browser TVSDK sélectionne le taux le plus élevé en dessous du taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p><span class="codeph"> initialBitRate</span> renvoie une valeur entière qui représente le profil byte par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimal </td> 
   <td colname="col2">Le débit binaire le plus faible auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est inférieur à ce débit binaire. <p><span class="codeph"> minBitRate</span> renvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2">Débit binaire autorisé le plus élevé auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est supérieur à ce débit. <p><span class="codeph"> maxBitRate</span> renvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez les informations suivantes à l’esprit :

* Lorsque le débit binaire change, le navigateur TVSDK est distribué. `AdobePSDK.ProfileEvent` avec le type comme `AdobePSDK.PSDKEventType.PROFILE_CHANGED`.

* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous définissez une plage de 300000 à 2000000, le TVSDK du navigateur prend uniquement en compte les profils 1, 2 et 3. Les applications peuvent ainsi s’adapter à diverses conditions réseau, telles que le passage de la connexion Wi-Fi à la technologie 3G ou à divers appareils tels qu’un téléphone, une tablette ou un ordinateur de bureau.

Pour définir les paramètres de contrôle ABR :

* Définissez les paramètres de la variable `ABRControlParameters` classe .

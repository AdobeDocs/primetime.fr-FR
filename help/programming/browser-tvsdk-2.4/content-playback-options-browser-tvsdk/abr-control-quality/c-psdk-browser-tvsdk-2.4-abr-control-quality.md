---
description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. Le navigateur TVSDK peut sélectionner le niveau de qualité de chaque rafale en fonction de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. Le navigateur TVSDK peut sélectionner le niveau de qualité de chaque rafale en fonction de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: 4c34fb7b-1bbd-4fa9-8929-d50e85a17396
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 1%

---


# Aperçu {#adaptive-bit-rates-abr-for-video-quality-overview}

Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. Le navigateur TVSDK peut sélectionner le niveau de qualité de chaque rafale en fonction de la bande passante disponible.

Le navigateur TVSDK surveille en permanence le débit binaire pour s’assurer que le contenu est lu à la vitesse de transmission optimale pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de commutation de débit binaire adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit binaire multiple (MBR). Le navigateur TVSDK bascule automatiquement sur le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2">Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lors des débuts de lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, le navigateur TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, le navigateur TVSDK sélectionne le taux le plus élevé en dessous du taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p><span class="codeph"> </span> initialBitRaterrenvoie un entier qui représente l’octet par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2">Le débit binaire le plus bas autorisé auquel l'ABR peut basculer. Le changement ABR ignore les profils dont le débit binaire est inférieur à ce débit binaire. <p><span class="codeph"> </span> minBitRaterrenvoie un entier qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2">Débit maximal autorisé auquel l'ABR peut basculer. Le changement ABR ignore les profils dont le débit est supérieur à ce débit binaire. <p><span class="codeph"> </span> maxBitRaterrenvoie un entier qui représente le profil bits par seconde. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* Lorsque le débit binaire change, le navigateur TVSDK distribue `AdobePSDK.ProfileEvent` avec le type `AdobePSDK.PSDKEventType.PROFILE_CHANGED`.

* Vous pouvez modifier vos paramètres d’ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1 : 300000
* 2 : 700000
* 3 : 1500000
* 4 : 2400000
* 5 : 4000000

Si vous spécifiez une plage de 300000 à 2000000, le navigateur TVSDK ne prend en compte que les profils 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, comme passer du wifi au 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

Pour définir les paramètres de contrôle ABR :

* Définissez les paramètres sur la classe `ABRControlParameters`.


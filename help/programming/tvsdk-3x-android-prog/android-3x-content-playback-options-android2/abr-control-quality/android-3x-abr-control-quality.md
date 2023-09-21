---
description: Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque rafale en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.
title: Taux de bits adaptatifs (ABR) pour la qualité vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Présentation {#adaptive-bit-rates-abr-for-video-quality-overview}

Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque rafale en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.

TVSDK contrôle constamment le débit afin de s’assurer que le contenu est lu à un débit optimal pour la connexion réseau actuelle. Vous pouvez définir la stratégie de changement de débit adaptatif (ABR) et les débits initiaux, minimaux et maximales pour un flux à débit multiple (MBR). TVSDK bascule automatiquement vers le débit qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. </p> <p>Au démarrage de la lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé en dessous du taux maximum. Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p><span class="codeph"> getABRInitialBitRate</span> renvoie une valeur entière qui représente le profil byte par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimal </td> 
   <td colname="col2"> <p>Le débit binaire le plus faible auquel l’ABR peut basculer. </p> <p>Le changement ABR ignore les profils dont le débit est inférieur à ce débit binaire. <span class="codeph"> getABRMinBitRate</span> renvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>Débit binaire autorisé le plus élevé auquel l’ABR peut basculer. </p> <p>Le changement ABR ignore les profils dont le débit est supérieur à ce débit. <span class="codeph"> getABRMaxBitRate</span> renvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Stratégie de changement ABR </td> 
   <td colname="col2"> <p>Lorsque cela est possible, la lecture passe progressivement au profil de débit le plus élevé. Vous pouvez définir la stratégie de changement d’ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les profils. La valeur par défaut est <span class="codeph"> ABR_MODERATE</span>. </p> <p>Lorsque TVSDK décide de basculer vers un débit supérieur, le lecteur sélectionne le profil de débit idéal sur lequel basculer en fonction de la stratégie ABR actuelle : 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>: passe au profil avec le débit supérieur suivant lorsque la bande passante est 50 % supérieure au débit actuel. </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>: passe au profil de débit supérieur suivant lorsque la bande passante est de 20 % supérieure au débit actuel. </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>: bascule immédiatement vers le profil de débit le plus élevé lorsque la bande passante est supérieure au débit actuel. </li> 
     </ul> </p> <p>Si le débit initial est nul ou n’est pas spécifié mais qu’une stratégie est spécifiée, la lecture commence par le profil de débit le plus faible pour une stratégie conservatrice, le profil le plus proche du débit médian des profils disponibles pour une stratégie modérée et le profil de débit le plus élevé pour une stratégie agressive. </p> <p>La stratégie fonctionne dans les contraintes des débits minimal et maximal, si ces débits sont spécifiés. </p> <p> <span class="codeph"> getABRPolicy</span> renvoie le paramètre actuel de la fonction <span class="codeph"> ABRControlParameters</span> enum : <span class="codeph"> ABR_CONSERVATIVE</span>, <span class="codeph"> ABR_MODERATE</span>, ou <span class="codeph"> ABR_AGGRESSIVE</span>. </p> <p>Pour plus d’informations, voir le document sur l’API Paramètres de contrôle ABR . </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez les informations suivantes à l’esprit :

* Le mécanisme de basculement TVSDK peut remplacer vos paramètres, car TVSDK favorise une expérience de lecture continue plutôt que de respecter strictement vos paramètres de contrôle.
* Lorsque le débit binaire change, TVSDK distribue `onProfileChanged` événements dans `PlaybackEventListener`.

* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous définissez une plage de 300000 à 2000000, TVSDK prend uniquement en compte les profils 1, 2 et 3. Les applications peuvent ainsi s’adapter à diverses conditions réseau, telles que le passage de la connexion Wi-Fi à la technologie 3G ou à divers appareils tels qu’un téléphone, une tablette ou un ordinateur de bureau.

Pour définir les paramètres de contrôle ABR, définissez les paramètres sur la variable `ABRControlParameter` classe .

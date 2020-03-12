---
description: Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: d41c3edf-33c7-4616-820f-22303d578df0
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#adaptive-bit-rates-abr-for-video-quality-overview}

Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.

TVSDK surveille constamment le débit binaire pour s’assurer que le contenu est lu au débit binaire optimal pour la connexion réseau actuelle. Vous pouvez définir la stratégie de commutation de débit adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit multiple (MBR). TVSDK bascule automatiquement vers le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. </p> <p>Lors de la  de lecture, le  le plus proche, qui est égal ou supérieur au débit initial, est utilisé pour le premier segment. Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le  avec le débit minimal supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé au-dessous du taux maximum. Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p><span class="codeph"> getABRInitialBitRate</span> renvoie une valeur entière qui représente le  d’octet par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2"> <p>Le débit binaire le plus faible auquel l’ABR peut basculer. </p> <p>Le basculement ABR ignore les  avec un débit binaire inférieur à ce débit binaire. <span class="codeph"> getABRMinBitRate</span> renvoie une valeur entière qui représente le  de bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>débit maximal autorisé auquel l’ABR peut basculer. </p> <p>Le basculement ABR ignore les  avec un débit binaire supérieur à ce débit binaire. <span class="codeph"> getABRMaxBitRate</span> renvoie une valeur entière qui représente le  de bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Stratégie de commutation ABR </td> 
   <td colname="col2"> <p>Lorsque cela est possible, la lecture bascule progressivement vers le  de débit le plus élevé. Vous pouvez définir la stratégie de commutation ABR, qui détermine la vitesse à laquelle TVSDK bascule d’un  à l’autre. La valeur par défaut est <span class="codeph"> ABR_MODERATE</span>. </p> <p>Lorsque TVSDK décide de basculer vers un débit plus élevé, le lecteur sélectionne le de débit idéal pour passer à la stratégie ABR actuelle : 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span>: Passe au  avec le débit supérieur suivant lorsque la bande passante est supérieure de 50 % à celle du débit actuel. </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span>: Passe au prochain de débit supérieur lorsque la bande passante est supérieure de 20 % à la vitesse de transmission actuelle. </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span>: Bascule immédiatement vers le de débit le plus élevé lorsque la bande passante est supérieure au débit actuel. </li> 
     </ul> </p> <p>Si le débit initial est égal à zéro ou n’est pas spécifié mais qu’une stratégie est spécifiée, le de lecture  avec le de débit le plus faible pour une stratégie conservatrice, letaux de bit le plus proche du débit médian dutaux disponible pour une stratégie modérée et le plus élevé pour une stratégie agressive. </p> <p>La stratégie fonctionne selon les contraintes des débits minimal et maximal, si ces débits sont spécifiés. </p> <p> <span class="codeph"> getABRPolicy</span> renvoie le paramètre actuel de l'énumération <span class="codeph"> ABRControlParameters</span> : <span class="codeph"> ABR_CONSERVATIVE</span>, <span class="codeph"> ABR_MODERATE</span>ou <span class="codeph"> ABR_AGGRESSIVE</span>. </p> <p>Pour plus d'informations, consultez le document API ABRControlParameters.</p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* Le mécanisme de basculement TVSDK peut remplacer vos paramètres, car TVSDK favorise une lecture continue plutôt que l’application stricte de vos paramètres de contrôle.
* Lorsque le débit binaire change, TVSDK distribue des  `onProfileChanged` dans `PlaybackEventListener`.

* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les  suivantes :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous spécifiez une plage de 300000 à 2000000, TVSDK ne prend en compte que les 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, comme passer du wifi au 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

Pour définir des paramètres de contrôle ABR, définissez les paramètres sur la `ABRControlParameter` classe.

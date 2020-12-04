---
description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: 87fd7d97-8d13-430d-a88e-bcbff8026679
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---


# Aperçu {#adaptive-bit-rates-abr-for-video-quality-overview}

Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction du niveau de mise en mémoire tampon actuel et de la bande passante disponible.

TVSDK surveille en permanence le débit binaire pour s’assurer que le contenu est lu à la vitesse de transmission optimale pour la connexion réseau actuelle. Vous pouvez définir la stratégie de commutation de débit binaire adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit binaire multiple (MBR). TVSDK bascule automatiquement sur le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. </p> <p>Lors des débuts de lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé inférieur au taux maximum. Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p><span class="codeph"> </span> getABRInitialBitRaterrenvoie une valeur entière qui représente l’octet par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2"> <p>Le débit binaire le plus bas autorisé auquel l'ABR peut basculer. </p> <p>Le changement ABR ignore les profils dont le débit binaire est inférieur à ce débit binaire. <span class="codeph"> </span> getABRMinBitRaterrenvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>Débit maximal autorisé auquel l'ABR peut basculer. </p> <p>Le changement ABR ignore les profils dont le débit est supérieur à ce débit binaire. <span class="codeph"> </span> getABRMaxBitRaterrenvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Stratégie de commutation ABR </td> 
   <td colname="col2"> <p>Lorsque cela est possible, la lecture passe progressivement au profil de débit le plus élevé. Vous pouvez définir la stratégie de commutation ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les profils. La valeur par défaut est <span class="codeph"> ABR_MODERATE</span>. </p> <p>Lorsque TVSDK décide de basculer vers un débit binaire plus élevé, le lecteur sélectionne le profil de débit binaire idéal à utiliser en fonction de la stratégie ABR actuelle : 
     <ul id="ul_AC9C99D84A3B4A8DBD1A05CC05DEE771"> 
      <li id="li_B79C0AA2CBFB42FF98A257CEC9C400BA"><span class="codeph"> ABR_CONSERVATIVE</span> : Bascule vers le profil avec le débit binaire suivant plus élevé lorsque la bande passante est supérieure de 50 % à celle du débit binaire actuel. </li> 
      <li id="li_38CC3A95D8634F359D0F7C273D0108C0"><span class="codeph"> ABR_MODERATE</span> : Passe au profil de débit supérieur suivant lorsque la bande passante est supérieure de 20 % à celle du débit actuel. </li> 
      <li id="li_E845C035420D4B3FB2B179F448F8CA85"><span class="codeph"> ABR_AGGRESSIVE</span> : Bascule immédiatement vers le profil de débit le plus élevé lorsque la bande passante est supérieure au débit binaire actuel. </li> 
     </ul> </p> <p>Si le débit initial est nul ou n’est pas spécifié mais qu’une stratégie est spécifiée, les débuts de lecture avec le profil de débit le plus faible pour une stratégie conservatrice, le profil le plus proche du débit médian des profils disponibles pour une stratégie modérée et le profil de débit le plus élevé pour une stratégie agressive. </p> <p>La stratégie fonctionne dans les contraintes des débits minimum et maximum, si ces débits sont spécifiés. </p> <p> <span class="codeph"> </span> getABRPolicyrenvoie le paramètre actuel de  <span class="codeph"> </span> ABRControlParametersenum :  <span class="codeph"> ABR_CONSERVATIVE</span>,  <span class="codeph"> ABR_MODERATE</span> ou  <span class="codeph"> ABR_AGGRESSIVE</span>. </p> <p>Pour plus d'informations, consultez le document API Paramètres de contrôle ABR. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* Le mécanisme de basculement TVSDK peut remplacer vos paramètres, car TVSDK favorise une lecture continue plutôt que le respect strict des paramètres de contrôle.
* Lorsque le débit binaire change, TVSDK distribue `onProfileChanged` événements dans `PlaybackEventListener`.

* Vous pouvez modifier vos paramètres d’ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1 : 300000
* 2 : 700000
* 3 : 1500000
* 4 : 2400000
* 5 : 4000000

Si vous spécifiez une plage de 300000 à 2000000, TVSDK ne prend en compte que les profils 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, comme passer du wifi au 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

Pour définir des paramètres de contrôle ABR, définissez les paramètres sur la classe `ABRControlParameter`.
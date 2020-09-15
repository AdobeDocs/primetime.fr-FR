---
description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: e3d5ef90-067d-48e0-a025-081de931d842
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 0%

---


# Débit adaptatif (ABR) pour la qualité vidéo{#adaptive-bit-rates-abr-for-video-quality}

Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.

TVSDK surveille en permanence le débit binaire pour s’assurer que le contenu est lu à la vitesse de transmission optimale pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de commutation de débit binaire adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit binaire multiple (MBR). TVSDK bascule automatiquement sur le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lors des débuts de lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. </p> <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé inférieur au taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p> <span class="apiname"> ABRInitialBitRate </span> renvoie un entier qui représente l'octet par seconde par profil. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2"> <p>Le débit binaire le plus bas autorisé auquel l'ABR peut basculer. Le changement ABR ignore les profils dont le débit binaire est inférieur à ce débit binaire. </p> <p> <span class="apiname"> ABRMinBitRate </span> renvoie un entier qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>Débit maximal autorisé auquel l'ABR peut basculer. Le changement ABR ignore les profils dont le débit est supérieur à ce débit binaire. </p> <p> <span class="apiname"> ABRMaxBitRate </span> renvoie un entier qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Stratégie de commutation ABR </td> 
   <td colname="col2"> Lorsque cela est possible, la lecture passe progressivement au profil de débit le plus élevé. Vous pouvez définir la stratégie de commutation ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les profils. La valeur par défaut est <span class="codeph"> MODERATE_POLICY </span>. <p>Lorsque TVSDK décide de basculer vers un débit binaire plus élevé, le lecteur sélectionne le profil de débit binaire idéal à utiliser en fonction de la stratégie ABR actuelle : 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>: Bascule vers le profil avec le débit binaire suivant plus élevé lorsque la bande passante est supérieure de 50 % à celle du débit binaire actuel. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>: Passe au profil de débit supérieur suivant lorsque la bande passante est supérieure de 20 % à celle du débit actuel. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY </span>: Bascule immédiatement vers le profil de débit le plus élevé lorsque la bande passante est supérieure au débit binaire actuel. </li> 
     </ul> </p> <p>Si le débit initial est égal à zéro ou n’est pas spécifié, mais qu’une stratégie est spécifiée, les débuts de lecture avec le profil de débit le plus faible pour les versions conservatrices, le profil le plus proche du débit médian des profils disponibles pour les versions modérées et le profil de débit le plus élevé pour les versions agressives. </p> <p>La stratégie fonctionne dans les contraintes des débits minimum et maximum, si ces débits sont spécifiés. </p> <p> <span class="codeph"> ABRPolicy </span> renvoie le paramètre actuel de l' <span class="codeph"> énumération </span> ABRControlParameters : CONSERVATIVE_POLICY, MODERATE_POLICY ou AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* Le mécanisme de basculement TVSDK peut remplacer vos paramètres, car TVSDK favorise une lecture continue plutôt que le respect strict des paramètres de contrôle.
* Lorsque le débit binaire change, TVSDK est distribué `ProfileEvent.PROFILE_CHANGED`.
* Vous pouvez modifier vos paramètres d’ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous spécifiez une plage de 300000 à 2000000, TVSDK ne prend en compte que les profils 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, comme passer du wifi au 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

Pour définir les paramètres de contrôle ABR, effectuez l&#39;une des opérations suivantes :

* Utilisez la classe `ABRControlParameterBuilder` helper pour définir n&#39;importe quel sous-ensemble des paramètres (fonctionne `ABRControlParameter` en arrière-plan).

* Définissez les paramètres de la `ABRControlParameter` classe.

## Configuration des débits adaptatifs à l’aide de ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069}

L&#39;utilisation de la classe `ABRControlParametersBuilder` helper est la méthode la plus simple et la plus efficace pour définir les paramètres ABR.

* Le `ABRControlParametersBuilder` constructeur définit tous les paramètres ABR sur les valeurs par défaut de l&#39;objet `ABRControlParameters` sous-jacent.

* Vous pouvez réinitialiser des paramètres ABR individuels au cours de l’exécution, à condition de conserver une référence à la même `ABRControlParametersBuilder` instance.

Cette classe inclut également la méthode `toABRControlParameters()` helper. Utilisez cette méthode pour obtenir une instance de `ABRControlParameters` et la définir sur la `mediaPlayer.ABRControlParameters` propriété. Vos paramètres entrent ainsi en vigueur dans le lecteur.

1. Instanciez la classe `ABRControlParametersBuilder` helper et définissez les paramètres sur Media Player.

   >[!NOTE]
   >
   >Par exemple, l’exemple suivant initialise tous les paramètres par défaut, puis définit uniquement la stratégie sur conservateur et limite le débit maximal à 1000000 :
   >
   >
   ```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```

1. Modifiez les paramètres ABR individuels au moment de l’exécution.

   Pour modifier des paramètres individuels tout en conservant les autres paramètres tels qu’ils étaient :

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Pour conserver vos paramètres précédents, vous devez conserver une référence à la même `ABRControlParametersBuilder` instance que celle créée à l’étape 1.

## Configuration des débits adaptatifs à l&#39;aide des paramètres ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec `ABRControlParameters`, mais vous pouvez en construire une nouvelle à tout moment.

Cette capacité de définir des paramètres d&#39;ABR a été prise en charge avant l&#39;existence de la `ABRControlParametersBuilder` classe, mais elle est toujours efficace pour définir des paramètres d&#39;ABR au moment de la construction. Cependant, pour modifier des paramètres individuels après la construction, vous devez utiliser la `ABRControlParametersBuilder` classe.

Les conditions suivantes s&#39;appliquent à `ABRControlParameters`:

* Vous devez fournir des valeurs pour tous les paramètres au moment de la construction.
* Vous ne pouvez pas modifier les valeurs individuelles après la construction.
* Si les paramètres que vous spécifiez se trouvent en dehors de la plage autorisée, un `ArgumentError` est généré.

1. Déterminez les débits initiaux, minimaux et maximaux.
1. Déterminez la stratégie ABR :

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. Définissez les valeurs des paramètres ABR dans le `ABRControlParameters` constructeur et affectez-les au lecteur Media.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```


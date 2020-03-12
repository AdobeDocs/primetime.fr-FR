---
description: Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: e3d5ef90-067d-48e0-a025-081de931d842
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Débit adaptatif (ABR) pour la qualité vidéo{#adaptive-bit-rates-abr-for-video-quality}

Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.

TVSDK surveille constamment le débit binaire pour s’assurer que le contenu est lu au débit binaire optimal pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de commutation de débit binaire adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit binaire multiple (MBR). TVSDK bascule automatiquement vers le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lors de la  de lecture, le  le plus proche, qui est égal ou supérieur au débit initial, est utilisé pour le premier segment. </p> <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le  avec le débit minimal supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé au-dessous du taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p> <span class="apiname"> ABRInitialBitRate </span> renvoie un nombre entier qui représente le  d’octet par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2"> <p>Le débit binaire le plus faible auquel l’ABR peut basculer. Le basculement ABR ignore les  avec un débit binaire inférieur à ce débit binaire. </p> <p> <span class="apiname"> ABRMinBitRate </span> renvoie un entier qui représente le  de bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>débit maximal autorisé auquel l’ABR peut basculer. Le basculement ABR ignore les  avec un débit binaire supérieur à ce débit binaire. </p> <p> <span class="apiname"> ABRMaxBitRate </span> renvoie un entier qui représente le  de bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Stratégie de commutation ABR </td> 
   <td colname="col2"> Lorsque cela est possible, la lecture bascule progressivement vers le  de débit le plus élevé. Vous pouvez définir la stratégie de commutation ABR, qui détermine la vitesse à laquelle TVSDK bascule d’un  à l’autre. La valeur par défaut est <span class="codeph"> MODERATE_POLICY </span>. <p>Lorsque TVSDK décide de basculer vers un débit plus élevé, le lecteur sélectionne le de débit idéal pour passer à la stratégie ABR actuelle : 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>: Passe au  avec le débit supérieur suivant lorsque la bande passante est supérieure de 50 % à celle du débit actuel. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>: Passe au prochain de débit supérieur lorsque la bande passante est supérieure de 20 % à la vitesse de transmission actuelle. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY </span>: Bascule immédiatement vers le de débit le plus élevé lorsque la bande passante est supérieure au débit actuel. </li> 
     </ul> </p> <p>Si le débit initial est égal à zéro ou n’est pas spécifié, mais qu’une stratégie est spécifiée, le de lecture  avec le de débit le plus faible pour le mode conservateur, le  le plus proche du débit médian dutaux disponible pour le mode modéré et le plus élevé pour le mode agressif. </p> <p>La stratégie fonctionne selon les contraintes des débits minimal et maximal, si ces débits sont spécifiés. </p> <p> <span class="codeph"> ABRPolicy </span> renvoie le paramètre actuel de l' <span class="codeph"> énumération ABRControlParameters </span> : CONSERVATIVE_POLICY, MODERATE_POLICY ou AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* Le mécanisme de basculement TVSDK peut remplacer vos paramètres, car TVSDK favorise une lecture continue plutôt que l’application stricte de vos paramètres de contrôle.
* Lorsque le débit change, TVSDK est distribué `ProfileEvent.PROFILE_CHANGED`.
* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les  suivantes :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous spécifiez une plage de 300000 à 2000000, TVSDK ne prend en compte que les 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, comme passer du wifi au 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

Pour définir les paramètres de contrôle ABR, effectuez l’une des opérations suivantes :

* Utilisez la classe `ABRControlParameterBuilder` helper pour définir n’importe quel sous-ensemble des paramètres (fonctionne `ABRControlParameter` en arrière-plan).

* Définissez les paramètres sur la `ABRControlParameter` classe.

## Configuration des débits adaptatifs à l’aide d’ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069}

L&#39;utilisation de la classe `ABRControlParametersBuilder` helper est la méthode la plus simple et la plus efficace pour définir des paramètres ABR.

* Le `ABRControlParametersBuilder` constructeur définit tous les paramètres ABR sur les valeurs par défaut de l’objet `ABRControlParameters` sous-jacent.

* Vous pouvez réinitialiser des paramètres ABR individuels pendant l’exécution, à condition de conserver une référence à la même `ABRControlParametersBuilder` instance.

Cette classe inclut également la méthode `toABRControlParameters()` d’assistance. Utilisez cette méthode pour obtenir une instance de `ABRControlParameters` et la définir sur la `mediaPlayer.ABRControlParameters` propriété. Vos paramètres sont alors appliqués au lecteur.

1. Instanciez la classe `ABRControlParametersBuilder` d’assistance et définissez les paramètres sur le lecteur Media.

   >[!NOTE]
   >
   >Par exemple, l’exemple suivant initialise tous les paramètres par défaut, puis définit uniquement la stratégie sur conservateur et limite le débit maximal à 1000000 :    >
   >
   >
   ```>
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```   >
   >



1. Modifiez les paramètres ABR individuels au moment de l’exécution.

   Pour modifier des paramètres individuels tout en laissant le reste des paramètres tels qu’ils étaient :

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Pour conserver vos paramètres précédents, vous devez conserver une référence à la même `ABRControlParametersBuilder` instance que celle créée à l’étape 1.

## Configuration des débits adaptatifs à l’aide de ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483}

Vous pouvez définir des valeurs de contrôle ABR uniquement avec `ABRControlParameters`, mais vous pouvez en construire une nouvelle à tout moment.

Cette capacité de définir des paramètres ABR était prise en charge avant l&#39;existence de la `ABRControlParametersBuilder` classe, mais elle est toujours efficace pour définir des paramètres ABR au moment de la construction. Cependant, pour modifier des paramètres individuels après la construction, vous devez utiliser la `ABRControlParametersBuilder` classe.

Les conditions suivantes s’appliquent à `ABRControlParameters`:

* Vous devez fournir des valeurs pour tous les paramètres au moment de la construction.
* Vous ne pouvez pas modifier les valeurs individuelles après la construction.
* Si les paramètres que vous spécifiez ne sont pas compris dans la plage autorisée, une `ArgumentError` valeur est générée.

1. Déterminez les débits initial, minimal et maximal.
1. Déterminer la stratégie ABR :

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. Définissez les valeurs des paramètres ABR dans le `ABRControlParameters` constructeur et affectez-les au lecteur multimédia.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```


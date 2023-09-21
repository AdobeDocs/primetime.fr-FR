---
description: Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque rafale en fonction de la bande passante disponible.
title: Taux de bits adaptatifs (ABR) pour la qualité vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 0%

---

# Taux de bits adaptatifs (ABR) pour la qualité vidéo{#adaptive-bit-rates-abr-for-video-quality}

Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque rafale en fonction de la bande passante disponible.

TVSDK contrôle constamment le débit afin de s’assurer que le contenu est lu à un débit optimal pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de changement de débit adaptatif (ABR) et les débits initiaux, minimaux et maximales pour un flux à débit multiple (MBR). TVSDK bascule automatiquement vers le débit qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. Au démarrage de la lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. </p> <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé en dessous du taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> <p> <span class="apiname"> ABRInitialBitRate </span> renvoie une valeur entière qui représente le profil byte par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimal </td> 
   <td colname="col2"> <p>Le débit binaire le plus faible auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est inférieur à ce débit binaire. </p> <p> <span class="apiname"> ABRMinBitRate </span> renvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>Débit binaire autorisé le plus élevé auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est supérieur à ce débit. </p> <p> <span class="apiname"> ABRMaxBitRate </span> renvoie une valeur entière qui représente le profil bits par seconde. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Stratégie de changement ABR </td> 
   <td colname="col2"> Lorsque cela est possible, la lecture passe progressivement au profil de débit le plus élevé. Vous pouvez définir la stratégie de changement d’ABR, qui détermine la vitesse à laquelle TVSDK bascule entre les profils. La valeur par défaut est <span class="codeph"> MODERATE_POLICY </span>. <p>Lorsque TVSDK décide de basculer vers un débit supérieur, le lecteur sélectionne le profil de débit idéal sur lequel basculer en fonction de la stratégie ABR actuelle : 
     <ul id="ul_058D0FFC944C476A83BB9E756B95DEBD"> 
      <li id="li_C690A12DC34C4754B01C2D0616FB6A0A"> <span class="codeph"> CONSERVATIVE_POLICY </span>: passe au profil avec le débit supérieur suivant lorsque la bande passante est 50 % supérieure au débit actuel. </li> 
      <li id="li_FF5BDB099B554940AC296938C7A12B81"> <span class="codeph"> MODERATE_POLICY </span>: passe au profil de débit supérieur suivant lorsque la bande passante est de 20 % supérieure au débit actuel. </li> 
      <li id="li_E602508429864C279BF78360E95718A6"> <span class="codeph"> AGGRESSIVE_POLICY </span>: bascule immédiatement vers le profil de débit le plus élevé lorsque la bande passante est supérieure au débit actuel. </li> 
     </ul> </p> <p>Si le débit initial est nul ou n’est pas spécifié, mais qu’une stratégie est spécifiée, la lecture commence par le profil de débit le plus faible pour les profils conservateurs, le profil le plus proche du débit médian des profils disponibles pour les profils modérés et le profil de débit le plus élevé pour les profils agressifs. </p> <p>La stratégie fonctionne dans les contraintes des débits minimal et maximal, si ces débits sont spécifiés. </p> <p> <span class="codeph"> ABRPolicy </span> renvoie le paramètre actuel de la fonction <span class="codeph"> ABRControlParameters </span> enum : CONSERVATIVE_POLICY, MODERATE_POLICY ou AGGRESSIVE_POLICY. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez les informations suivantes à l’esprit :

* Le mécanisme de basculement TVSDK peut remplacer vos paramètres, car TVSDK favorise une expérience de lecture continue plutôt que de respecter strictement vos paramètres de contrôle.
* Lorsque le débit binaire change, TVSDK distribue `ProfileEvent.PROFILE_CHANGED`.
* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous définissez une plage de 300000 à 2000000, TVSDK prend uniquement en compte les profils 1, 2 et 3. Les applications peuvent ainsi s’adapter à diverses conditions réseau, telles que le passage de la connexion Wi-Fi à la technologie 3G ou à divers appareils tels qu’un téléphone, une tablette ou un ordinateur de bureau.

Pour définir les paramètres de contrôle ABR, effectuez l’une des opérations suivantes :

* Utilisez la variable `ABRControlParameterBuilder` classe d’assistance pour définir n’importe quel sous-ensemble des paramètres (fonctionne sur `ABRControlParameter` en coulisses)

* Définissez les paramètres de la variable `ABRControlParameter` classe .

## Configuration des taux de bits adaptatifs à l’aide d’ABRControlParametersBuilder {#section_3DDE397A7CE445E1832EBAA46CE5C069}

En utilisant la variable `ABRControlParametersBuilder` La classe d’assistance est la méthode la plus simple et la plus efficace pour définir des paramètres ABR.

* La variable `ABRControlParametersBuilder` Le constructeur définit tous les paramètres ABR sur les valeurs par défaut sur le sous-jacent `ABRControlParameters` .

* Vous pouvez réinitialiser des paramètres ABR individuels au moment de l’exécution, à condition de conserver une référence au même `ABRControlParametersBuilder` instance.

Cette classe inclut également la variable `toABRControlParameters()` méthode d’assistance. Utilisez cette méthode pour obtenir une instance de `ABRControlParameters` et définissez-le sur le `mediaPlayer.ABRControlParameters` . Cela entraîne l’entrée en vigueur de vos paramètres dans le lecteur.

1. Instanciation de la variable `ABRControlParametersBuilder` de la classe d’assistance, puis définissez les paramètres sur le lecteur Media.

   >[!NOTE]
   >
   >Par exemple, l’exemple suivant initialise tous les paramètres par défaut, puis définit uniquement la stratégie sur conservatrice et limite le débit maximal à 1000000 :
   >
   >```
   >var abrBuilder:ABRControlParametersBuilder =  
   >   new ABRControlParametersBuilder(); 
   >abrBuilder.policy = ABRControlParameters.CONSERVATIVE_POLICY; 
   >abrBuilder.maxBitRate = 1000000; 
   >mediaPlayer.abrControlParameters =  
   >   abrBuilder.toABRControlParameters();
   >```
   >

1. Modifiez des paramètres ABR individuels au moment de l’exécution.

   Pour modifier des paramètres individuels tout en conservant le reste des paramètres tels qu’ils étaient :

   ```
   // If later you want to reset the max bit rate to 2000000 
   abrBuilder.maxBitRate = 2000000; 
   mediaPlayer.abrControlParameters =  
     abrBuilder.toABRControlParameters();
   ```

   Pour conserver vos paramètres précédents, vous devez conserver une référence à la même `ABRControlParametersBuilder` instance créée à l’étape 1.

## Configuration des taux de bits adaptatifs à l’aide d’ABRControlParameters {#section_02161FD0A73F40ED9CAE17F9AF850483}

Vous ne pouvez définir des valeurs de contrôle ABR qu’avec `ABRControlParameters`, mais vous pouvez en construire un nouveau à tout moment.

Cette possibilité de définir des paramètres ABR était prise en charge avant l’existence de la fonction `ABRControlParametersBuilder` , mais cette fonctionnalité est toujours efficace pour définir les paramètres ABR au moment de la construction. Toutefois, pour modifier des paramètres individuels après la construction, vous devez utiliser la variable `ABRControlParametersBuilder` classe .

Les conditions suivantes s&#39;appliquent à `ABRControlParameters`:

* Vous devez fournir des valeurs pour tous les paramètres au moment de la construction.
* Vous ne pouvez pas modifier les valeurs individuelles après l’heure de construction.
* Si les paramètres que vous spécifiez se trouvent en dehors de la plage autorisée, une `ArgumentError` est généré.

1. Décidez des débits initial, minimal et maximal.
1. Déterminer la stratégie ABR :

   * `CONSERVATIVE_POLICY`
   * `MODERATE_POLICY`
   * `AGGRESSIVE_POLICY`

1. Définissez les valeurs du paramètre ABR dans la variable `ABRControlParameters` constructeur et affectez-les au lecteur multimédia.

   ```
   mediaPlayer.abrControlParameters = new ABRControlParameters( 
       ABRControlParameters.CONSERVATIVE_POLICY, 
       0, // Initial bit rate 
       0, // Minimum bit rate 
       1000000 // Maximum bit rate 
   );
   ```

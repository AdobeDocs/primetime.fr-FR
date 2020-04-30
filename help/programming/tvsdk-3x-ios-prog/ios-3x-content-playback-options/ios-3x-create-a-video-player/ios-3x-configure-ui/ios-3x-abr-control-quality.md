---
description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: a9b9a6a8-4098-4952-90e7-684e64800b3f
translation-type: tm+mt
source-git-commit: a63768e51c911914a6ba9d884e2587fa34939f9d

---


# Débit adaptatif (ABR) pour la qualité vidéo {#adaptive-bit-rates-abr-for-video-quality}

Les flux HLS et DASH fournissent différents encodages de débit binaire (profils) pour la même courte rafale vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.

TVSDK surveille en permanence le débit binaire pour s’assurer que le contenu est lu à la vitesse de transmission optimale pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de commutation de débit binaire adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit binaire multiple (MBR). TVSDK bascule automatiquement sur le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lors des débuts de lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. </p> <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé inférieur au taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2"> <p>Le débit binaire le plus bas autorisé auquel l'ABR peut basculer. Le changement ABR ignore les profils dont le débit binaire est inférieur à ce débit binaire. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>Débit maximal autorisé auquel l'ABR peut basculer. Le changement ABR ignore les profils dont le débit est supérieur à ce débit binaire. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* TVSDK ne distribue pas de événements de commutation de débit binaire.
* Vous pouvez modifier vos paramètres d’ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous spécifiez une plage de 300000 à 2000000, TVSDK ne prend en compte que les profils 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, telles que le passage du Wi-Fi à la technologie 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

## Configuration des débits adaptatifs {#section_572FCE4CC28D4DF8BD9C461F00B3CA17}

Pour configurer les paramètres de débit binaire adaptatif TVSDK :

1. Configurez une instance de `PTABRControlParameters` pour définir les paramètres de débit initial, minimal et maximal.

   Les valeurs par défaut sont affichées dans le fragment de code suivant, mais votre application peut définir n’importe quelle valeur entière pour chacun de ces paramètres.

   >[!IMPORTANT]
   >
   >Spécifiez les paramètres de débit binaire en bits par seconde (bit/s).

   ```
   // ARC (add autorelease for non-ARC) 
   PTABRControlParameters *abrMetaData =  
       [[PTABRControlParameters alloc] init];  
   
   abrMetaData.initialBitRate = -1; 
   abrMetaData.minBitRate = 0; 
   abrMetaData.maxBitRate = INT_MAX;
   ```

1. Mettez à jour votre `PTMediaPlayer` instance avec l’ `PTABRControlParameters` instance configurée.

   ```
   // assuming self.player is the PTMediaPlayer instance 
   self.player.abrControlParameters = abrMetaData;
   ```

Souvenez-vous des points suivants :

* L’application doit définir la `abrControlParameters` propriété sur `PTMediaPlayer` avant de configurer une `PTMediaPlayerItem` instance pour que les paramètres de débit initial et minimal soient appliqués.

   Après les débuts de lecture du contenu, la définition d’une nouvelle instance affecte uniquement le paramètre de débit maximal.

* Pour mettre à jour le paramètre de débit maximal pendant la lecture, créez une `PTABRControlParameters` instance et définissez-la sur l’instance du lecteur.
* Vous pouvez mettre à jour le paramètre de débit maximal pendant la lecture uniquement sur iOS 8.0 et versions ultérieures. Pour les versions antérieures, la `maxBitrate` valeur définie avant le démarrage de la lecture du contenu est utilisée.
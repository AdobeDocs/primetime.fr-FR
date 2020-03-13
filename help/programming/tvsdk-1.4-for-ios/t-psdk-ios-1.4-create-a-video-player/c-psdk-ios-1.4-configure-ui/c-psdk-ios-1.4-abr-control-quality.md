---
description: Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-description: Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.
seo-title: Débit adaptatif (ABR) pour la qualité vidéo
title: Débit adaptatif (ABR) pour la qualité vidéo
uuid: e5752d7e-fa7d-407c-96df-c3830a35c66e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Débit adaptatif (ABR) pour la qualité vidéo{#adaptive-bit-rates-abr-for-video-quality}

Les flux HLS et DASH fournissent des encodages de débit binaire () différents pour la même petite explosion vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque éclatement en fonction de la bande passante disponible.

TVSDK surveille constamment le débit binaire pour s’assurer que le contenu est lu au débit binaire optimal pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de commutation de débit binaire adaptatif (ABR) et les débits initiaux, minimaux et maximaux pour un flux à débit binaire multiple (MBR). TVSDK bascule automatiquement vers le débit binaire qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. Lors de la  de lecture, le  le plus proche, qui est égal ou supérieur au débit initial, est utilisé pour le premier segment. </p> <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le  avec le débit minimal supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé au-dessous du taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimum </td> 
   <td colname="col2"> <p>Le débit binaire le plus faible auquel l’ABR peut basculer. Le basculement ABR ignore les  avec un débit binaire inférieur à ce débit binaire. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>débit maximal autorisé auquel l’ABR peut basculer. Le basculement ABR ignore les  avec un débit binaire supérieur à ce débit binaire. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les informations suivantes :

* TVSDK ne distribue pas de  de commutation de débit binaire.
* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les  suivantes :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous spécifiez une plage de 300000 à 2000000, TVSDK ne prend en compte que les 1, 2 et 3. Cela permet aux applications de s&#39;adapter à diverses conditions réseau, comme le passage du Wi-Fi au 3G ou à divers périphériques tels qu&#39;un téléphone, une tablette ou un ordinateur de bureau.

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

Tenez compte des points suivants :

* L’application doit définir la `abrControlParameters` propriété `PTMediaPlayer` avant de configurer une `PTMediaPlayerItem` instance pour que les paramètres de débit initial et minimal prennent effet.

   Une fois le de lecture de contenu , la définition d’une nouvelle instance affecte uniquement le paramètre de débit maximal.

* Pour mettre à jour le paramètre de débit maximal pendant la lecture, créez une `PTABRControlParameters` instance et définissez-la sur l’instance du lecteur.
* Vous pouvez mettre à jour le paramètre de débit maximal pendant la lecture uniquement sur iOS 8.0 et versions ultérieures. Pour les versions antérieures, la `maxBitrate` valeur définie avant le démarrage de la lecture du contenu est utilisée.


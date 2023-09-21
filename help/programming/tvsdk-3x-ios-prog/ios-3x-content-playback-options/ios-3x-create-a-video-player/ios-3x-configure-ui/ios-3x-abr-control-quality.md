---
description: Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque rafale en fonction de la bande passante disponible.
title: Taux de bits adaptatifs (ABR) pour la qualité vidéo
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Taux de bits adaptatifs (ABR) pour la qualité vidéo {#adaptive-bit-rates-abr-for-video-quality}

Les flux HLS et DASH fournissent différents codages (profils) de débit binaire pour la même courte rafale de vidéo. TVSDK peut sélectionner le niveau de qualité pour chaque rafale en fonction de la bande passante disponible.

TVSDK contrôle constamment le débit afin de s’assurer que le contenu est lu à un débit optimal pour la connexion réseau actuelle.

Vous pouvez définir la stratégie de changement de débit adaptatif (ABR) et les débits initiaux, minimaux et maximales pour un flux à débit multiple (MBR). TVSDK bascule automatiquement vers le débit qui offre la meilleure expérience de lecture dans la configuration spécifiée.

<table id="table_AF838E082235406AA359BF1C1A77F85F"> 
 <tbody> 
  <tr> 
   <td colname="col01"> Débit initial </td> 
   <td colname="col2"> <p>Débit de lecture souhaité (en bits par seconde) pour le premier segment. Au démarrage de la lecture, le profil le plus proche, égal ou supérieur au débit initial, est utilisé pour le premier segment. </p> <p> Si un débit minimal est défini et que le débit initial est inférieur au débit minimal, TVSDK sélectionne le profil dont le débit minimal est supérieur au débit minimal. Si le taux initial est supérieur au taux maximum, TVSDK sélectionne le taux le plus élevé en dessous du taux maximum. </p> <p>Si le débit initial est nul ou non défini, le débit initial est déterminé par la stratégie ABR. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit minimal </td> 
   <td colname="col2"> <p>Le débit binaire le plus faible auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est inférieur à ce débit binaire. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col01"> Débit maximal </td> 
   <td colname="col2"> <p>Débit binaire autorisé le plus élevé auquel l’ABR peut basculer. Le changement ABR ignore les profils dont le débit est supérieur à ce débit. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez les informations suivantes à l’esprit :

* TVSDK ne distribue pas d’événements à partir du changement de débit.
* Vous pouvez modifier vos paramètres ABR à tout moment et le lecteur bascule pour utiliser le profil qui correspond le mieux aux paramètres les plus récents.

Par exemple, si un flux comporte les profils suivants :

* 1: 300000
* 2: 700000
* 3: 1500000
* 4: 2400000
* 5: 4000000

Si vous définissez une plage de 300000 à 2000000, TVSDK prend uniquement en compte les profils 1, 2 et 3. Les applications peuvent ainsi s’adapter à diverses conditions réseau, telles que le passage du Wi-Fi à la technologie 3G ou à divers appareils tels qu’un téléphone, une tablette ou un ordinateur de bureau.

## Configuration des taux de bits adaptatifs {#section_572FCE4CC28D4DF8BD9C461F00B3CA17}

Pour configurer les paramètres de débit binaire adaptatif TVSDK :

1. Configuration d’une instance de `PTABRControlParameters` pour définir les paramètres de débit initial, minimal et maximal.

   Les valeurs par défaut sont affichées dans le fragment de code suivant, mais votre application peut définir n’importe quelle valeur entière pour chacun de ces paramètres.

   >[!IMPORTANT]
   >
   >Spécifiez les paramètres de débit en bits par seconde (bit/s).

   ```
   // ARC (add autorelease for non-ARC) 
   PTABRControlParameters *abrMetaData =  
       [[PTABRControlParameters alloc] init];  
   
   abrMetaData.initialBitRate = -1; 
   abrMetaData.minBitRate = 0; 
   abrMetaData.maxBitRate = INT_MAX;
   ```

1. Mettez à jour votre `PTMediaPlayer` avec l’instance configurée `PTABRControlParameters` instance.

   ```
   // assuming self.player is the PTMediaPlayer instance 
   self.player.abrControlParameters = abrMetaData;
   ```

Gardez à l’esprit les éléments suivants :

* L’application doit définir la variable `abrControlParameters` sur `PTMediaPlayer` avant de configurer une `PTMediaPlayerItem` pour que les paramètres de débit initial et minimal prennent effet.

  Une fois la lecture du contenu lancée, la définition d’une nouvelle instance affecte uniquement le paramètre de débit maximal.

* Pour mettre à jour le paramètre de débit maximal pendant la lecture, créez une `PTABRControlParameters` et définissez-le sur l’instance du lecteur.
* Vous pouvez mettre à jour le paramètre de débit maximal pendant la lecture uniquement sur iOS 8.0 et versions ultérieures. Pour les versions antérieures, la variable `maxBitrate` qui a été définie avant le démarrage de la lecture du contenu est utilisée.

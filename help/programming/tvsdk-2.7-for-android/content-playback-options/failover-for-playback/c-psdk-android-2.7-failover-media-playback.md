---
description: Pour les médias en direct et vidéo à la demande (VOD), le TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture du débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.
seo-description: Pour les médias en direct et vidéo à la demande (VOD), le TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture du débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.
seo-title: Lecture et basculement du média
title: Lecture et basculement du média
uuid: 5189cef4-ee09-43b3-ae3d-1052fc535480
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Lecture et basculement du média {#media-playback-and-failover}

Pour les médias en direct et vidéo à la demande (VOD), le TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture du débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_4EA0AEFA7FB84FCEA699DFB10B135368}

Lorsqu’une liste de lecture entière est absente, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, TVSDK tente de récupérer. S’il est impossible de le récupérer, l’application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution intermédiaire est absente, TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, le TVSDK  télécharger la liste de lecture des variantes et les segments à partir de la position correspondante. Si le lecteur ne trouve pas la même liste de lecture de résolution, il tentera de passer en revue d’autres listes de lecture à débit binaire et leurs variantes. Un débit immédiatement inférieur est le premier choix, puis sa variante, etc. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, TVSDK ira au débit supérieur et compte en bas à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Vous pouvez, par exemple, fermer le lecteur  le  du et diriger l’utilisateur vers le de  de de catalogue. Le  d’intérêt est le `STATUS_CHANGED` , et le rappel correspondant est la `onStatusChanged` méthode. Le code suivant contrôle si le lecteur change son état interne en `ERROR`:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## Basculement de segment manquant {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

Lorsqu’un segment est manquant, par exemple lorsqu’un segment particulier ne parvient pas à être téléchargé, TVSDK tente de récupérer par le biais de diverses tentatives de basculement. S’il ne parvient pas à récupérer, une erreur est générée.

Si un segment est manquant sur le serveur, car, par exemple, le fichier manifeste n’est pas présent, le segment ne peut pas être téléchargé, etc., TVSDK tente d’échouer en tentant d’exécuter les options suivantes :

1. Tentez un basculement vers le même segment, au même débit, dans un fichier de variante.
1. Passez à un autre débit (commutateur ABR) dans le même fichier.
1. Parcourez tous les débits disponibles dans chaque variante disponible.
1. Ignorez le segment et émettez un avertissement.

Lorsque TVSDK ne parvient pas à obtenir un autre segment, il déclenche une notification d’ `CONTENT_ERROR` erreur. Cette notification contient une notification interne avec le `DOWNLOAD_ERROR` code. Si le flux avec le problème est une autre piste audio, TVSDK génère la notification `AUDIO_TRACK_ERROR` d’erreur.

Si le moteur vidéo ne parvient pas à obtenir en continu les segments, il limite les sauts de segments continus à 5, après quoi la lecture est arrêtée et TVSDK émet une erreur `NATIVE_ERROR` avec le code 5.

>[!NOTE]
>
>Voici quelques restrictions que vous devez connaître : >
>* Les paramètres de contrôle de débit binaire adaptatif (ABR) ne sont pas pris en compte lorsqu’un basculement survient.
>
>  
En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit leur de débit binaire, comme flux de sauvegarde.
>* Lors d’une opération de basculement, il peut y avoir un commutateur .
>
>  
Si une erreur se produit lors du téléchargement d’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit minimal/maximal autorisé sont ignorés.



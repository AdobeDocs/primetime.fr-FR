---
description: Pour les médias en direct et vidéo à la demande (VOD), TVSDK démarre la lecture en téléchargeant la liste de lecture associée au débit de résolution moyenne et télécharge les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture de débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.
title: Lecture et basculement du média
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# Lecture et basculement du média {#media-playback-and-failover}

Pour les médias en direct et vidéo à la demande (VOD), TVSDK démarre la lecture en téléchargeant la liste de lecture associée au débit de résolution moyenne et télécharge les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture de débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_4EA0AEFA7FB84FCEA699DFB10B135368}

Lorsqu’une liste de lecture entière est manquante, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur ne se télécharge pas, TVSDK tente de récupérer. S’il ne peut pas être récupéré, votre application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution intermédiaire est manquante, TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, TVSDK commence à télécharger la liste de lecture des variantes et les segments à partir de la position correspondante. Si le lecteur ne trouve pas la même liste de lecture de résolution, il tente de parcourir d’autres listes de lecture à débit binaire et leurs variantes. Un débit inférieur immédiat est le premier choix, puis sa variante, etc. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, TVSDK accède au débit supérieur et compte à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Par exemple, vous pouvez fermer l’activité du lecteur et diriger l’utilisateur vers l’activité de catalogue. L’événement ciblé est le suivant : `STATUS_CHANGED` et le rappel correspondant est `onStatusChanged` . Voici le code qui surveille si le lecteur change son état interne en `ERROR`:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## Basculement des segments manquant {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment particulier échoue, TVSDK tente de récupérer par le biais de diverses tentatives de basculement. S’il ne peut pas récupérer, une erreur s’affiche.

Si un segment est manquant sur le serveur, car, par exemple, le fichier de manifeste n’est pas présent, le segment ne peut pas être téléchargé, etc., TVSDK tente d’échouer en tentant d’effectuer les options suivantes :

1. Tenter un basculement vers le même segment, au même débit, dans un fichier de variante.
1. Basculez vers un autre débit binaire (bouton ABR) dans le même fichier.
1. Parcourez tous les débits disponibles dans chaque variante disponible.
1. Ignorez le segment et générez un avertissement.

Lorsque TVSDK ne parvient pas à obtenir un autre segment, il déclenche une `CONTENT_ERROR` notification d’erreur. Cette notification contient une notification interne avec la variable `DOWNLOAD_ERROR` code. Si la diffusion contenant le problème est une autre piste audio, TVSDK génère la variable `AUDIO_TRACK_ERROR` notification d’erreur.

Si le moteur vidéo ne parvient pas à obtenir des segments en continu, il limite les sauts de segment continus à 5, après quoi la lecture est arrêtée et TVSDK émet une `NATIVE_ERROR` avec le code 5.

>[!NOTE]
>
>Voici quelques restrictions que vous devez connaître :
>
>* Les paramètres de contrôle de débit adaptatif (ABR) ne sont pas pris en compte lors d’un basculement.
>
>  En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit son profil de débit, comme flux de sauvegarde.
>* Lors d’une opération de basculement, il peut y avoir un commutateur de profil.
>
>  Si une erreur se produit lors du téléchargement de l’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit binaire min/max autorisé sont ignorés.
>

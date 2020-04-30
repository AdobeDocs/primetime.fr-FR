---
description: Pour les médias à la demande en direct et vidéo, TVSDK permet la lecture des débuts en téléchargeant la liste de lecture associée au débit de résolution moyenne et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture des débits haute résolution et les médias associés et poursuit le processus de téléchargement.
seo-description: Pour les médias à la demande en direct et vidéo, TVSDK permet la lecture des débuts en téléchargeant la liste de lecture associée au débit de résolution moyenne et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture des débits haute résolution et les médias associés et poursuit le processus de téléchargement.
seo-title: Lecture et basculement du média
title: Lecture et basculement du média
uuid: e0072eeb-8ad1-436f-bf4a-fee6885a25bd
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Lecture et basculement du média {#media-playback-and-failover}

Pour les médias à la demande en direct et vidéo, TVSDK permet la lecture des débuts en téléchargeant la liste de lecture associée au débit de résolution moyenne et en téléchargeant les segments de médias définis par cette liste de lecture. Il sélectionne rapidement la liste de lecture des débits haute résolution et les médias associés et poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_4EA0AEFA7FB84FCEA699DFB10B135368}

Lorsqu’une sélection complète est manquante, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, TVSDK tente de récupérer. S’il est impossible de le récupérer, votre application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution moyenne est manquante, TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, TVSDK début le téléchargement de la liste de lecture de la variante et des segments à partir de la position correspondante. Si le lecteur ne trouve pas la même liste de lecture de résolution, il tentera de passer en revue d’autres listes de lecture à débit binaire et leurs variantes. Un débit immédiatement inférieur est le premier choix, puis sa variante, et ainsi de suite. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, TVSDK va aller au débit supérieur et compter à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Par exemple, vous pouvez fermer l’activité du lecteur et diriger l’utilisateur vers l’activité du catalogue. Le événement d’intérêt est le `STATUS_CHANGED` événement et le rappel correspondant est la `onStatusChanged` méthode. Voici le code qui surveille si le lecteur change son état interne en `ERROR`:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## Basculement de segment manquant {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

Lorsqu’un segment est manquant, par exemple lorsqu’un téléchargement d’un segment donné échoue, TVSDK tente de récupérer par le biais de plusieurs tentatives de basculement. S’il ne peut pas récupérer, une erreur est générée.

Si un segment est manquant sur le serveur, car, par exemple, le fichier manifeste n’est pas présent, le segment ne peut pas être téléchargé, etc., TVSDK tente d’échouer en tentant d’exécuter les options suivantes :

1. Tentez un basculement sur incident vers le même segment, au même débit, dans un fichier de variante.
1. Basculez vers un autre débit binaire (commutateur ABR) dans le même fichier.
1. Parcourez chaque débit disponible dans chaque variante disponible.
1. Ignorez le segment et émettez un avertissement.

Lorsque TVSDK ne parvient pas à obtenir un autre segment, il déclenche une notification d’ `CONTENT_ERROR` erreur. Cette notification contient une notification interne avec le `DOWNLOAD_ERROR` code. Si le flux présentant le problème est une autre piste audio, TVSDK génère la notification d’ `AUDIO_TRACK_ERROR` erreur.

Si le moteur vidéo ne parvient pas à obtenir des segments en permanence, il limite les sauts de segments continus à 5, après quoi la lecture est arrêtée et TVSDK émet une erreur `NATIVE_ERROR` avec le code 5.

>[!Rrestrictions]
>
>Voici quelques restrictions que vous devez connaître :
>* Les paramètres de contrôle de débit binaire adaptatif (ABR) ne sont pas pris en compte lorsqu’un basculement survient.
>
>  
En effet, le mécanisme de basculement est conçu pour utiliser n’importe laquelle des listes de lecture actuellement disponibles, quel que soit leur profil de débit binaire, comme flux de sauvegarde.
>* Lors d&#39;une opération de basculement, il peut y avoir un commutateur de profil.
>
>  
Si une erreur se produit lors du téléchargement d’un des segments de la liste de lecture, les paramètres de contrôle ABR tels que le débit minimal/maximal autorisé sont ignorés.
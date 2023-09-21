---
description: Pour les médias en direct et VOD, le navigateur TVSDK démarre la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire, puis en téléchargeant les segments du média de débit de résolution intermédiaire défini par la liste de lecture.
title: Lecture du média
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Lecture du média {#media-playback}

Pour les médias en direct et VOD, le navigateur TVSDK démarre la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire, puis en téléchargeant les segments du média de débit de résolution intermédiaire défini par la liste de lecture.

Le navigateur TVSDK sélectionne rapidement la liste de lecture de débit haute résolution et les médias associés, puis poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_81A5822C108449E1A0E94A6E25DE9E8E}

Lorsqu’une liste de lecture entière est manquante, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur ne se télécharge pas, le navigateur TVSDK tente de récupérer. S’il ne peut pas être récupéré, votre application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution intermédiaire est manquante, le navigateur TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, il commence à télécharger la liste de lecture des variantes et les segments à partir de la position correspondante. Si le TVSDK du navigateur ne trouve pas la même liste de lecture de résolution, il tente de parcourir d’autres listes de lecture à débit binaire et leurs variantes. Un débit inférieur immédiat est le premier choix, puis sa variante, etc. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, le TVSDK du navigateur passe au débit supérieur et compte à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Par exemple, vous pouvez fermer l’activité du lecteur et diriger l’utilisateur vers l’activité de catalogue. L’événement d’intérêt correspond à l’événement d’état ou de changement d’état, et le rappel correspondant à la méthode on status changed. Voici le code qui surveille si le lecteur change son état interne en ERROR :

```js
case AdobePSDK.MediaPlayerStatus.ERROR:  
var errorDesc = event.metadata.getValue('DESCRIPTION'); 
console.log(errorDesc); 
break; 
```

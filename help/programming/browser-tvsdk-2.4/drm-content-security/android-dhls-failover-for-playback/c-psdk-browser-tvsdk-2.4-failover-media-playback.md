---
description: Pour les médias en direct et VOD, le navigateur TVSDK début la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire, puis en téléchargeant les segments du support de débit de résolution intermédiaire définis par la liste de lecture.
seo-description: Pour les médias en direct et VOD, le navigateur TVSDK début la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire, puis en téléchargeant les segments du support de débit de résolution intermédiaire définis par la liste de lecture.
seo-title: Lecture multimédia
title: Lecture multimédia
uuid: 454f84fe-8077-4f37-8e62-1d6ba0fcde27
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# Lecture du média {#media-playback}

Pour les médias en direct et VOD, le navigateur TVSDK début la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire, puis en téléchargeant les segments du support de débit de résolution intermédiaire définis par la liste de lecture.

Le navigateur TVSDK sélectionne rapidement la liste de lecture à débit binaire haute résolution et les médias associés et poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_81A5822C108449E1A0E94A6E25DE9E8E}

Lorsqu’il manque une sélection complète, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, le navigateur TVSDK tente de récupérer. S’il est impossible de le récupérer, votre application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution moyenne est manquante, le navigateur TVSDK recherche une liste de lecture de variante à la même résolution. S’il trouve la même résolution, il début de télécharger la liste de lecture de variantes et les segments à partir de la position correspondante. Si le navigateur TVSDK ne trouve pas la même liste de lecture de résolution, il tentera de passer en revue d’autres listes de lecture à débit binaire et leurs variantes. Un débit immédiatement inférieur est le premier choix, puis sa variante, et ainsi de suite. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, le navigateur TVSDK ira au débit supérieur et comptera à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Par exemple, vous pouvez fermer l’activité du lecteur et diriger l’utilisateur vers l’activité du catalogue. Le événement d’intérêt est le événement modifié de l’état ou du statut, et le rappel correspondant est la méthode on status changed. Voici le code qui surveille si le lecteur change son état interne en ERROR :

```js
case AdobePSDK.MediaPlayerStatus.ERROR:  
var errorDesc = event.metadata.getValue('DESCRIPTION'); 
console.log(errorDesc); 
break; 
```

---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
seo-description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
seo-title: Lecture et basculement
title: Lecture et basculement
uuid: 5d75e55d-9c01-4a36-9bdf-891289821c6b
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Lecture et basculement {#playback-and-failover}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.

Primetime ne peut pas se protéger des défaillances telles que la panne d&#39;un FAI ou la déconnexion d&#39;un câble. Toutefois, la diffusion en flux continu Primetime offre une protection contre le basculement afin de protéger la lecture de certaines défaillances du serveur distant ou de certaines défaillances opérationnelles, ce qui améliore l’expérience des utilisateurs. Le navigateur TVSDK met en oeuvre une protection contre le basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture fluide malgré les problèmes de transmission. Le lecteur vidéo bascule automatiquement vers une visionneuse de supports de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.

## Lecture multimédia {#media-playback}

Pour les médias en direct et VOD, le navigateur TVSDK  la lecture en téléchargeant la liste de lecture associée au débit de résolution intermédiaire, puis en téléchargeant les segments du média de débit de résolution intermédiaire défini par la liste de lecture.

Le navigateur TVSDK sélectionne rapidement la liste de lecture à débit binaire haute résolution et les médias associés et poursuit le processus de téléchargement.

## Basculement de la liste de lecture manquant {#section_81A5822C108449E1A0E94A6E25DE9E8E}

Lorsqu’une liste de lecture entière est absente, par exemple, lorsque le fichier M3U8 spécifié dans un fichier manifeste de niveau supérieur n’est pas téléchargé, le navigateur TVSDK tente de récupérer. S’il est impossible de le récupérer, l’application détermine l’étape suivante.

Si la liste de lecture associée au débit de résolution intermédiaire est absente, le navigateur TVSDK recherche une variante de liste de lecture à la même résolution. S’il trouve la même résolution, il  télécharger la liste de lecture des variantes et les segments à partir de la position correspondante. Si le navigateur TVSDK ne trouve pas la même liste de lecture de résolution, il tentera de passer en revue d’autres listes de lecture à débit binaire et leurs variantes. Un débit immédiatement inférieur est le premier choix, puis sa variante, etc. Si toutes les listes de lecture à débit inférieur et leurs variantes sont épuisées dans la tentative de trouver une liste de lecture valide, le navigateur TVSDK ira au débit supérieur et comptera à partir de là. Si une liste de lecture valide est introuvable, le processus échoue et le lecteur passe à l’état ERROR.

Votre application peut déterminer comment gérer cette situation. Vous pouvez, par exemple, fermer le lecteur  le  du et diriger l’utilisateur vers le de  de de catalogue. Le  d’intérêt est le  d’état ou le modifié, et le rappel correspondant est la méthode on status changed. Le code suivant contrôle si le lecteur change son état interne en ERROR :

```js
case AdobePSDK.MediaPlayerStatus.ERROR:  
var errorDesc = event.metadata.getValue('DESCRIPTION'); 
console.log(errorDesc); 
break; 
```

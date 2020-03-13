---
description: Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq  pleine bande passante pour une expérience utilisateur plus riche.
seo-description: Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq  pleine bande passante pour une expérience utilisateur plus riche.
seo-title: Format AC-3 5.1
title: Format AC-3 5.1
uuid: 11dab0ac-5aed-4909-b9fb-807781f88480
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Format AC-3 5.1 {#ac-format}

Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq  pleine bande passante pour une expérience utilisateur plus riche.

Pour plus d’informations, voir [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

TVSDK prend en charge les fonctionnalités AC-3 5.1 suivantes :

* Audio surround AC-3
* Flux mixtes/non mixtes pour le type audio surround
* Possibilité d’ du périphérique afin de voir si le codec audio surround est disponible sur le périphérique.

   Les résultats déterminent le type de codec audio préféré sélectionné. Le manifeste avec le type de codec audio que le périphérique ne va pas utiliser est ignoré. Par exemple, si le format AC-3 a été sélectionné, les  avec le format Advanced Audio Coding (AAC) ne sont pas prises en compte.
* Mode de transmission

   En mode passthrough, au lieu de décoder le média du format AC-3 5.1 vers un format PCM (multicanal pulse-code modulation), le TVSDK est modifié ou non (selon le périphérique) du support Dolby du décodeur. Ce média est envoyé au périphérique audio (haut-parleur ou récepteur) afin que le périphérique audio puisse décoder et lire le flux Dolby Suround.

>[!IMPORTANT]
>
>TVSDK prend en charge les fonctionnalités AC-3 5.1 uniquement sur l’appareil Amazon Fire TV 1ère génération.

Les fonctionnalités AC-3 5.1 suivantes ne sont pas prises en charge :

* Audio AAC multicanal
* ABR sur différents codecs (AAC - AC3)

## Sélectionner le média pris en charge {#section_0D7E717BE18B418D817EE017EF2375D1}

Voici le flux de travail typique qui se produit lorsque TVSDK trouve un manifeste avec des supports AC-3 et AAC :

1. Le TVSDK  quel codec le périphérique peut prendre en charge.
1. Le codec de qualité supérieure est sélectionné.

   Voici l’ordre dans lequel la qualité est sélectionnée :

   1. AC-3
   1. AAC

1. TVSDK ignore les  avec d’autres types de codec audio.

>[!TIP]
>
>L’application ne peut pas obtenir d’informations sur les  ignorées.

## Détermination du mode de sortie {#section_D2AFBF33D3904AC2A7C653A60C3A0CD3}

Lors du traitement d’un média AC-3, si un périphérique Android est connecté au système d’enceintes, la décision de lire le contenu en mode Surround ou stéréo dépend de la configuration du périphérique.

|  | Bruit ambiant | Haut-parleur stéréo |
|---|---|---|
| Configuration du périphérique Dolby on (ou auto) | Configuration du périphérique Dolby on (ou auto) | Mode stéréo |
| Configuration du périphérique Dolby désactivée | Mode stéréo | Mode stéréo |


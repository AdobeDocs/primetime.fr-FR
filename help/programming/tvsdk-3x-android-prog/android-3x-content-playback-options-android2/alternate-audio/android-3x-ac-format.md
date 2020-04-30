---
description: Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq canaux de bande passante complète pour une expérience utilisateur plus riche.
seo-description: Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq canaux de bande passante complète pour une expérience utilisateur plus riche.
seo-title: Format AC-3 5.1
title: Format AC-3 5.1
uuid: 9d1adf33-4c9b-4d31-8212-ac301f3e44c5
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Format AC-3 5.1 {#ac-format}

Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq canaux de bande passante complète pour une expérience utilisateur plus riche.

Pour plus d’informations, voir [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

TVSDK prend en charge les fonctionnalités AC-3 5.1 suivantes :

* Audio surround AC-3
* Flux mixtes/non mixtes pour le type audio surround
* Possibilité de requête du périphérique pour savoir si le codec audio surround est disponible sur le périphérique.

   Les résultats déterminent quel type de codec audio préféré est sélectionné. Le manifeste avec le type de codec audio que le périphérique ne va pas utiliser est ignoré. Par exemple, si le format AC-3 a été sélectionné, les profils au format Advanced Audio Coding (AAC) ne sont pas pris en compte.
* Mode de transmission

   En mode passthrough, au lieu de décoder le support du format AC-3 5.1 vers un format PCM (multicanal pulse-code modulation), TVSDK est modifié ou non modifié (selon l&#39;appareil) par le support Dolby du décodeur. Ce média est envoyé au périphérique audio (haut-parleur ou récepteur) afin que le périphérique audio puisse décoder et lire le flux Dolby surround.

>[!IMPORTANT]
>
>TVSDK prend en charge les fonctionnalités AC-3 5.1 uniquement sur l’appareil Amazon Fire TV 1ère génération.

Les fonctionnalités AC-3 5.1 suivantes ne sont pas prises en charge :

* Audio AAC multicanal
* ABR sur différents codecs (AAC - AC3)

## Sélectionner le média pris en charge {#section_0D7E717BE18B418D817EE017EF2375D1}

Voici le flux de travail typique qui se produit lorsque TVSDK trouve un manifeste avec un média AC-3 et AAC :

1. requêtes TVSDK qui codent le périphérique peut prendre en charge.
1. Le codec de meilleure qualité est sélectionné.

   Voici l&#39;ordre dans lequel la qualité est sélectionnée :

   1. AC-3
   1. AAC

1. TVSDK ignore les profils avec d’autres types de codec audio.

>[!TIP]
>
>L&#39;application ne peut pas obtenir d&#39;informations sur les profils ignorés.

## Détermination du mode de sortie {#section_D2AFBF33D3904AC2A7C653A60C3A0CD3}

Lors du traitement d’un média AC-3, si un périphérique Android est connecté au système de haut-parleur, la décision de lire le contenu en mode surround ou stéréo dépend de la manière dont le périphérique est configuré.

|  | **Bruit ambiant** | **Haut-parleur stéréo** |
|---|---|---|
| Configuration du périphérique Dolby on (ou auto) | Configuration du périphérique Dolby on (ou auto) | Mode stéréo |
| Configuration du périphérique Dolby désactivée | Mode stéréo | Mode stéréo |
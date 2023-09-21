---
description: Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq canaux pleine bande passante pour une expérience utilisateur plus riche.
title: Format AC-3 5.1
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Format AC-3 5.1 {#ac-format}

Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq canaux pleine bande passante pour une expérience utilisateur plus riche.

Pour plus d’informations, voir [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

TVSDK prend en charge les fonctionnalités AC-3 5.1 suivantes :

* Audio entouré d’un appareil AC-3
* Diffusions mixtes/non mixtes pour le type audio entouré
* Possibilité d’effectuer des requêtes sur l’appareil pour voir si le codec audio entouré est disponible sur l’appareil.

  Les résultats déterminent le type de codec audio préféré sélectionné. Le manifeste avec le type de codec audio que l’appareil ne va pas utiliser est ignoré. Par exemple, si le format AC-3 a été sélectionné, les profils au format Advanced Audio Coding (AAC) ne sont pas pris en compte.
* Mode de transfert

  En mode passthrough, au lieu de dédécoder le média du format AC-3 5.1 vers un format PCM (pulsation-code multicanal), le TVSDK est modifié ou non modifié (en fonction de l’appareil) à partir du décodeur. Ce média est envoyé à l’appareil audio (haut-parleur ou récepteur) afin que l’appareil audio puisse décoder et lire le flux Dolby Suround.

>[!IMPORTANT]
>
>TVSDK ne prend en charge les fonctionnalités AC-3 5.1 que sur l’appareil Amazon Fire TV 1ère génération.

Les fonctionnalités AC-3 5.1 suivantes ne sont pas prises en charge :

* Audio AAC multicanal
* ABR dans différents codecs (AAC - AC3)

## Sélectionner le média pris en charge {#section_0D7E717BE18B418D817EE017EF2375D1}

Voici le workflow type qui se produit lorsque TVSDK trouve un manifeste avec AC-3 et AAC Media :

1. Requêtes TVSDK qui codent l’appareil pouvant être pris en charge.
1. Le codec de meilleure qualité est sélectionné.

   Voici l’ordre dans lequel la qualité est sélectionnée :

   1. AC-3
   1. AAC

1. TVSDK ignore les profils avec d’autres types de codec audio.

>[!TIP]
>
>L’application ne peut pas obtenir d’informations sur les profils ignorés.

## Déterminer le mode de sortie {#section_D2AFBF33D3904AC2A7C653A60C3A0CD3}

Lors du traitement d’un média AC-3, si un appareil Android est connecté au système de haut-parleur, la décision de lire le contenu en mode Suround ou stéréo dépend de la configuration de l’appareil.

|   | **Bruit de quartier** | **Haut-parleur stéréo** |
|---|---|---|
| Configuration du périphérique Dolby on (ou auto) | Configuration du périphérique Dolby on (ou auto) | Mode stéréo |
| Configuration du périphérique Dolby désactivée | Mode stéréo | Mode stéréo |

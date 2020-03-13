---
description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
seo-description: La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.
seo-title: Format AC-3 5.1
title: Format AC-3 5.1
uuid: d5e77bb5-ed51-4f9f-b34f-e9082f5ee4de
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Format AC-3 5.1{#ac-format}

La diffusion en continu sur Internet nécessite une connexion constante et stable pour lire un flux à partir d’un serveur distant. Cependant, la variabilité de la connexion Internet ou de la lecture en flux continu d’une visionneuse signifie que la lecture à distance peut ne pas avoir la qualité du média lu localement.

Primetime ne peut pas se protéger des défaillances telles que la panne d&#39;un FAI ou la déconnexion d&#39;un câble. Toutefois, la diffusion en flux continu Primetime offre une protection contre le basculement afin de protéger la lecture de certaines défaillances du serveur distant ou de certaines défaillances opérationnelles, ce qui améliore l’expérience des utilisateurs. TVSDK met en oeuvre une protection contre le basculement afin de minimiser les interruptions de lecture et d’obtenir une lecture fluide malgré les problèmes de transmission. Le lecteur vidéo bascule automatiquement vers une visionneuse de supports de sauvegarde lorsque des rendus ou des fragments entiers ne sont pas disponibles.

Le format Audio Codec 3 (AC-3, également appelé Dolby Digital®) 5.1, permet aux fournisseurs de contenu de compresser la taille des fichiers audio multicanaux sans nuire à la qualité du son. AC-3 est un format 5.1, ce qui signifie qu’il fournit cinq  pleine bande passante pour une expérience utilisateur plus riche.

Pour plus d’informations, voir [Dolby Digital 5.1](https://www.dolby.com/us/en/technologies/dolby-digital.html).

>[!IMPORTANT]
>
>TVSDK version 1.4 ne prend en charge le format AC-3 5.1 que sur Amazon FireTV.

TVSDK prend en charge les fonctionnalités AC-3 5.1 suivantes :

* Audio surround AC-3
* Flux mixtes/non mixtes pour le type audio surround
* Possibilité d’ du périphérique afin de voir si le codec audio surround est disponible sur le périphérique.

   Les résultats déterminent le type de codec audio préféré sélectionné. Le manifeste avec le type de codec audio que le périphérique ne va pas utiliser est ignoré. Par exemple, si le format AC-3 a été sélectionné, les  avec le format Advanced Audio Coding (AAC) ne sont pas prises en compte.
* Mode de transmission

   En mode passthrough, au lieu de décoder le média du format AC-3 5.1 vers un format PCM (multicanal pulse-code modulation), le TVSDK est modifié ou non (selon le périphérique) du support Dolby du décodeur. Ce média est envoyé au périphérique audio (haut-parleur ou récepteur) afin que le périphérique audio puisse décoder et lire le flux Dolby Suround.

TVSDK prend en charge les fonctionnalités AC-3 5.1 uniquement sur l’appareil Amazon Fire TV 1ère génération.

Les fonctionnalités AC-3 5.1 suivantes ne sont pas prises en charge :

* Audio AAC multicanal
* ABR sur différents codecs (AAC - AC3)

## Sélection des médias pris en charge {#section_E1DFA1F472EA4BDE846C71A3343E275A}

Voici le flux de travail typique qui se produit lorsque TVSDK trouve un manifeste avec des supports AC-3 et AAC :

1. Le TVSDK  quel codec le périphérique peut prendre en charge.
1. Le codec de qualité supérieure est sélectionné.

   L&#39;ordre de qualité est AC-3 > AAC.
1. TVSDK ignore les  avec d’autres types de codec audio.

>[!TIP]
>
>L’application ne peut pas obtenir d’informations sur les  ignorées.

## Détermination du mode de sortie {#section_64145D9824594C36AADBF0482C528767}

Lors du traitement d’un média AC-3, si un périphérique Android est connecté au système d’enceintes, la décision de lire le contenu en mode Surround ou stéréo dépend de la configuration du périphérique.

|  | Bruit ambiant | Haut-parleur stéréo |
|---|---|---|
| Configuration du périphérique Dolby on (ou auto) | Configuration du périphérique Dolby on (ou auto) | Mode stéréo |
| Configuration du périphérique Dolby désactivée | Mode stéréo | Mode stéréo |


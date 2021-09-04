---
title: Notes de mise à jour de Primetime
description: Notes de mise à jour de Primetime
copied-description: true
exl-id: 29087a3e-f16e-4510-8d3a-ed2229700899
source-git-commit: 97a192ed1d0ddc034f72a836a70293acfcca9881
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 32%

---

# Notes de mise à jour de Primetime

Bienvenue dans les notes de mise à jour d’Adobe Primetime. Les documents répertoriés dans le volet de navigation de gauche fournissent des informations spécifiques à la version, les exigences du système, les limitations, les problèmes résolus et les problèmes connus.

## Améliorations et correctifs de l’API 21.8.1

Cette version comprend la prise en charge des flux DASH en direct/linéaire.

Pour obtenir d’autres correctifs et détails, voir [Notes de mise à jour Ad Insertion](/help/release-notes/ptai-21x-release-notes.md)

## Améliorations et correctifs de TVSDK 3.13 iOS

Cette version introduit la prise en charge des publicités &quot;HLS/CMAF&quot; (préroll, midroll et postroll) DEMUXED pour les diffusions LIVE, VOD et FER.

Pour obtenir d’autres correctifs et détails, voir [Notes de mise à jour de TVSDK pour iOS](../release-notes/tvsdk-3x-ios.md)

## Correctifs dans TVSDK 3.13 Android

Cette version fournit une solution au problème du blocage de la diffusion Widevine DRM ou de l’affichage d’images noires sur les interrupteurs ABR sur les appareils FireTV, notamment Fire TV 3e génération pendant et Fire TV Cube 1ère et 2e génération.

Pour résoudre le problème, définissez l’API `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` pour les appareils Fire TV spécifiés avant de lancer la lecture. La valeur par défaut est false.

Pour plus d’informations, consultez les [Notes de mise à jour de TVSDK pour Android](../release-notes/tvsdk-3x-android.md) .

## Voir aussi

| Guide de l’utilisateur | Description |
|--- |--- |
| [Aide à la programmation sur Primetime](/help/programming/home.md) | Ce guide vous apprend à développer des applications et des lecteurs vidéo à l’aide de Java pour les appareils Android et d’Objective-C pour les appareils iOS. |
| [Aide sur la migration et la conversion de Primetime](/help/migration-guides/home.md) | Décrit le processus de conversion et de migration permettant de passer de la suite Primetime TVSDK existante à la suite de nouvelle génération. |
| [Implémentation de référence](/help/android-reference-implementation/home.md) | Permet de comprendre le TVSDK et de modifier les gestionnaires de fonctionnalités pour personnaliser votre lecteur personnel. |
| [Références de l’API Primetime](/help/reference/api-references.md) | Offre des informations détaillées sur les fonctions TVSDK, les structures de données et d’autres structures de programmation. |
| [Digital Rights Management](/help/digital-rights-management/home.md) | Permet d’en apprendre davantage sur divers scénarios de Digital Rights Management (DRM) |
| [Aide de Primetime Ad Insertion](/help/primetime-ad-insertion/home.md) | Explique comment monétiser du contenu en insérant sur le serveur des publicités dynamiques ciblées et en engageant l’audience grâce à des publicités personnalisées. |
| [Archives](https://helpx.adobe.com/primetime/archives.html) | Téléchargez des fichiers PDF de la documentation archivée. |

## Ressources utiles

* [Connaître Adobe Primetime](https://www.adobe.com/in/marketing/primetime.html)

* [Surveillance de simultanéité](https://tve.helpdocsonline.com/concurrency-monitoring-introduction)

* [Authentification Primetime](https://tve.helpdocsonline.com/home)

* [Forums Adobe Primetime DRM](https://forums.adobe.com/community/adobe_access)

* [Ressources pour les développeurs Adobe Primetime](https://www.adobe.com/devnet/primetime.html)

---
title: Notes de mise à jour de Primetime
description: Notes de mise à jour de Primetime
copied-description: true
translation-type: tm+mt
source-git-commit: 944bfb0f3bd0050a9d2974a37f4fabddaaac8a93
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 29%

---


# Notes de mise à jour de Primetime

Bienvenue dans les Notes de mise à jour Adobe Primetime. Les documents répertoriés dans le volet de navigation de gauche fournissent des informations spécifiques à la version, la configuration système requise, les limitations, les problèmes résolus et les problèmes connus.

## Améliorations et correctifs apportés à TVSDK 3.13 iOS

Cette version introduit la prise en charge des publicités &quot;HLS/CMAF&quot; (preroll, midroll et postroll) DÉMOXED pour les flux LIVE, VOD et FER.

Pour obtenir d’autres correctifs et détails, voir [Notes de mise à jour de TVSDK for iOS](../release-notes/tvsdk-3x-ios.md)

## Améliorations et correctifs de PTAI 21.2.2

Cette version comprend la prise en charge de l’insertion/synchronisation de flux EXT-X-IMAGE-STREAM-INF dans les flux HLS. La fonction est activée via une configuration côté serveur. Contactez votre gestionnaire de compte technique pour activer la fonction.

## Correctifs dans TVSDK 3.13 Android

Cette version offre une solution au problème du blocage du flux Widevine DRM ou de l&#39;affichage d&#39;images noires sur le commutateur ABR sur les appareils FireTV, qui incluent Fire TV 3e génération pendant et Fire TV Cube 1ère et 2e génération.

Pour résoudre ce problème, définissez l’API `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` pour les périphériques Fire TV spécifiés avant de commencer la lecture. La valeur par défaut est false.

Pour plus d’informations, consultez les [Notes de mise à jour de TVSDK for Android](../release-notes/tvsdk-3x-android.md).

## Améliorations et correctifs des notes de mise à jour de TVSDK 3.12 iOS

Cette version s’est concentrée sur la résolution des principaux problèmes des clients.

Consultez pour plus d’informations sur la version actuelle de [iOS](../release-notes/tvsdk-3x-ios.md).

## Voir aussi

| Guide de l’utilisateur | Description |
|--- |--- |
| [Aide à la programmation sur Primetime](/help/programming/home.md) | Ce guide vous apprend à développer des applications et des lecteurs vidéo à l’aide de Java pour les appareils Android et d’Objective-C pour les appareils iOS. |
| [Aide sur la migration et les conversions de Primetime](/help/migration-guides/home.md) | Décrit le processus de conversion et de migration permettant de passer de la suite Primetime TVSDK existante à la suite de nouvelle génération. |
| [Implémentation de référence](/help/android-reference-implementation/home.md) | Permet de comprendre le TVSDK et de modifier les gestionnaires de fonctionnalités pour personnaliser votre lecteur personnel. |
| [Références API Primetime](/help/reference/api-references.md) | Offre des informations détaillées sur les fonctions TVSDK, les structures de données et d’autres structures de programmation. |
| [Digital Rights Management](/help/digital-rights-management/home.md) | Permet d’en apprendre davantage sur divers scénarios de Digital Rights Management (DRM) |
| [Aide de Primetime Ad Insertion](/help/primetime-ad-insertion/home.md) | Explique comment monétiser du contenu en insérant sur le serveur des publicités dynamiques ciblées et en engageant l’audience grâce à des publicités personnalisées. |
| [Archives](https://helpx.adobe.com/primetime/archives.html) | Téléchargez des fichiers PDF de la documentation archivée. |

## Ressources utiles

* [Connaître Adobe Primetime](https://www.adobe.com/in/marketing/primetime.html)

* [Surveillance des conversions](https://tve.helpdocsonline.com/concurrency-monitoring-introduction)

* [Authentification Primetime](https://tve.helpdocsonline.com/home)

* [Forums DRM Adobe Primetime](https://forums.adobe.com/community/adobe_access)

* [Ressources pour les développeurs Adobe Primetime](https://www.adobe.com/devnet/primetime.html)

---
description: Pour que les sous-titres soient disponibles pour votre lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.
title: Exposer les sous-titres fermés
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# Exposer les sous-titres fermés {#expose-closed-captions}

Pour que les sous-titres soient disponibles pour votre lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.

Pour exposer des sous-titres fermés :

1. Dans `PTMediaPlayer` , définissez `closedCaptionDisplayEnabled` .

   Si l’utilisateur a activé les sous-titres, cette étape affiche le texte.

   >[!NOTE]
   >
   >L’utilisateur client active ou désactive le sous-titrage à l’aide des paramètres d’accessibilité d’iOS. Ces paramètres offrent également des options de mise en forme.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` est obsolète. Utilisation `subtitlesOptions` de `PTMediaPlayerItem`. Voir [Exposer les sous-titres](../../../tvsdk-3x-ios-prog/c-ios-closed-captioning-and-subtitles-ios/c-ios-closed-captioning-and-subtitles-reqts-ios/t-ios-subtitles-exposing-ios.md) pour utiliser des sous-titres non intégrés.

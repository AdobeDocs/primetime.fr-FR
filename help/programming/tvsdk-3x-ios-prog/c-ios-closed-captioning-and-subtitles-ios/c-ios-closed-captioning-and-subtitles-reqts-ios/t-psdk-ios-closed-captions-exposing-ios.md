---
description: Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.
title: Exposer les sous-titres fermés
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# Exposer les sous-titres fermés {#expose-closed-captions}

Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.

Pour exposer des sous-titres fermés :

1. Dans l&#39;objet `PTMediaPlayer`, définissez la propriété `closedCaptionDisplayEnabled`.

   Si l’utilisateur a activé les sous-titres, cette étape affiche le texte.

   >[!NOTE]
   >
   >L’utilisateur client active ou désactive le sous-titrage à l’aide des paramètres d’accessibilité iOS et ces paramètres offrent également des options de formatage.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` est désapprouvée. Utilisez la propriété `subtitlesOptions` de `PTMediaPlayerItem`. Voir [Exposer les sous-titres](../../../tvsdk-3x-ios-prog/c-ios-closed-captioning-and-subtitles-ios/c-ios-closed-captioning-and-subtitles-reqts-ios/t-ios-subtitles-exposing-ios.md) pour utiliser des sous-titres fermés.
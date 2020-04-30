---
description: Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.
seo-description: Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.
seo-title: Exposer les sous-titres fermés
title: Exposer les sous-titres fermés
uuid: 209b34ca-f14e-499e-af5f-2d8c7b359ef8
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# Exposer les sous-titres fermés {#expose-closed-captions}

Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.

Pour exposer des sous-titres fermés :

1. Dans `PTMediaPlayer` l’objet, définissez la `closedCaptionDisplayEnabled` propriété.

   Si l’utilisateur a activé les sous-titres, cette étape affiche le texte.

   >[!NOTE]
   >
   >L’utilisateur client active ou désactive le sous-titrage à l’aide des paramètres d’accessibilité iOS et ces paramètres offrent également des options de formatage.

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` est désapprouvée. Utilisez `subtitlesOptions` la propriété de `PTMediaPlayerItem`. Voir [Exposer les sous-titres](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) pour utiliser des sous-titres fermés.
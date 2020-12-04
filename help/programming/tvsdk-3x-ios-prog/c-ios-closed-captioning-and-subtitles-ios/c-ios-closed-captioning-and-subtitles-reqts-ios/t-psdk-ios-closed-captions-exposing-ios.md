---
description: Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.
seo-description: Pour que les sous-titres soient accessibles au lecteur client, vous devez les activer. L’utilisateur peut activer ou désactiver les sous-titres et sélectionner la mise en forme.
seo-title: Exposer les sous-titres fermés
title: Exposer les sous-titres fermés
uuid: 7057014a-b14a-4790-8f7f-37d7a1fb8194
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '143'
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
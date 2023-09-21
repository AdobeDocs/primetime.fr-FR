---
title: Liste autorisée pour les applications DRM Primetime autorisées à lire du contenu protégé
description: Liste autorisée pour les applications DRM Primetime autorisées à lire du contenu protégé
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Liste autorisée pour les applications DRM Primetime autorisées à lire du contenu protégé {#allowlist-for-primetime-drm-applications-allowed-to-play-protected-content}

Une liste autorisée spécifie les applications AIR, iOS et Android autorisées à lire du contenu. Il spécifie également les ID d’application AIR et iOS, la version minimale, la version maximale et l’ID d’éditeur.

Exemple de cas d’utilisation : utilisez cette règle pour limiter la lecture à une application spécifique, ou pour contrôler la version de l’application pouvant accéder au contenu.

>[!NOTE]
>
>Si vous utilisez Adobe Flash Builder pour créer des applications protégées, vous devez vous assurer de ne pas déployer l’application en mode de débogage. Lorsque vous déployez une application en mode de débogage, le Flash Builder est annexé. `.debug` à l’ID de l’application AIR, ce qui entraîne le comportement inattendu de la fonctionnalité de liste autorisée dans Primetime DRM.

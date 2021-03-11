---
title: Liste autorisée pour les applications DRM Primetime autorisée à lire du contenu protégé
description: Liste autorisée pour les applications DRM Primetime autorisée à lire du contenu protégé
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Liste autorisée pour les applications DRM Primetime autorisée à lire du contenu protégé {#allowlist-for-primetime-drm-applications-allowed-to-play-protected-content}

Une liste autorisée spécifie les applications AIR, iOS et Android autorisées à lire du contenu. Il spécifie également les ID d’application AIR et iOS, la version minimale, la version maximale et l’ID d’éditeur.

Exemple de cas d’utilisation : Utilisez cette règle pour limiter la lecture à une application particulière ou pour contrôler la version de l’application qui peut accéder au contenu.

>[!NOTE]
>
>Si vous utilisez Adobe Flash Builder pour créer des applications protégées, veillez à ne pas déployer l’application en mode de débogage. Lorsque vous déployez une application en mode de débogage, le Flash Builder ajoute `.debug` au ID de l&#39;application AIR, ce qui entraîne le comportement inattendu de la fonctionnalité de liste autorisée dans Primetime DRM.

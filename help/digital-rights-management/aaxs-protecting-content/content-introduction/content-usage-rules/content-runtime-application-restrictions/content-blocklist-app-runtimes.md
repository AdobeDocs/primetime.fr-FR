---
title: Liste bloquée des runtimes d'application limitée à l'accès au contenu protégé
description: Liste bloquée des runtimes d'application limitée à l'accès au contenu protégé
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Liste bloquée des runtimes d&#39;application limitée à l&#39;accès au contenu protégé {#blocklist-of-application-runtimes-restricted-from-accessing-protected-content}

Indique la version du Primetime ou du Flash Runtime qui ne peut pas accéder au contenu. Spécifiez le runtime restreint (Flash Player, AIR ou iOS), la plate-forme et la version.

Exemple de cas d’utilisation : Tout comme la liste bloquée client DRM, la dernière version des runtimes Flash Player, AIR ou iOS peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu.

Le runtime de l&#39;application peut être identifié par l&#39;un des attributs pris en charge pour les versions client DRM, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Correspondance exacte | Identifie le nom du runtime de l&#39;application. |

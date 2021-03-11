---
title: Liste bloquée des exécutions d’applications
description: Liste bloquée des exécutions d’applications
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Liste bloquée des runtimes d&#39;application {#blocklist-of-application-runtimes}

La liste bloquée des runtimes d&#39;application spécifie la version du client Primetime ou de l&#39;Runtime Flash qui ne peut pas accéder au contenu. Spécifiez le runtime restreint (Flash Player, AIR ou iOS), la plate-forme et la version.

Exemple de cas d’utilisation : Tout comme la liste bloquée client DRM de Primetime, la dernière version des runtimes Flash Player, AIR ou iOS peut être spécifiée comme la version minimale requise pour l&#39;acquisition de licence et la lecture de contenu.

Vous pouvez identifier l’exécution de l’application en fonction de l’un des attributs pris en charge pour les versions client DRM Primetime, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Correspondance exacte | Identifie le nom du runtime de l&#39;application. |


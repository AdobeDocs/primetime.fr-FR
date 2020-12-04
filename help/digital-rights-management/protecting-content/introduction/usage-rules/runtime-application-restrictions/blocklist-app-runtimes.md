---
description: 'null'
seo-description: 'null'
seo-title: Liste bloquée des exécutions d’applications
title: Liste bloquée des exécutions d’applications
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Liste bloquée des runtimes d&#39;application {#blocklist-of-application-runtimes}

La liste bloquée des runtimes d&#39;application spécifie la version du client Primetime ou de l&#39;Runtime Flash qui ne peut pas accéder au contenu. Spécifiez le runtime restreint (Flash Player, AIR ou iOS), la plate-forme et la version.

Exemple de cas d’utilisation : Tout comme la liste bloquée client DRM de Primetime, la dernière version des runtimes Flash Player, AIR ou iOS peut être spécifiée comme la version minimale requise pour l&#39;acquisition de licence et la lecture de contenu.

Vous pouvez identifier l’exécution de l’application en fonction de l’un des attributs pris en charge pour les versions client DRM Primetime, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Correspondance exacte | Identifie le nom du runtime de l&#39;application. |


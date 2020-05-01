---
description: 'null'
seo-description: 'null'
seo-title: Liste noire des runtimes d'application
title: Liste noire des runtimes d'application
uuid: fc3c9bd6-b1e6-4534-b29c-cd9a35b80928
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Liste noire des runtimes d&#39;application{#blacklist-of-application-runtimes}

La liste noire des runtimes d&#39;application spécifie la version du client Primetime ou du Flash Runtime qui ne peut pas accéder au contenu. Spécifiez le runtime restreint (Flash Player, AIR ou iOS), la plate-forme et la version.

Exemple de cas d’utilisation : Tout comme la liste noire du client DRM Primetime, la dernière version des runtimes Flash Player, AIR ou iOS peut être spécifiée comme la version minimale requise pour l&#39;acquisition de licence et la lecture de contenu.

Vous pouvez identifier l’exécution de l’application en fonction de l’un des attributs pris en charge pour les versions client DRM Primetime, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | `“FlashPlayer”, “AIR”, "DRM_Library", "AVE"` | Correspondance exacte | Identifie le nom du runtime de l&#39;application. |


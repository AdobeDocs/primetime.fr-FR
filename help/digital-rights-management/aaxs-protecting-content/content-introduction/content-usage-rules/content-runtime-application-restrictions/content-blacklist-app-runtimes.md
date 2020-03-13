---
seo-title: Liste noire des moteurs d’exécution d’application interdits d’accès au contenu protégé
title: Liste noire des moteurs d’exécution d’application interdits d’accès au contenu protégé
uuid: 462a2c09-b335-4768-bd0e-1359db169d69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Liste noire des moteurs d’exécution d’application interdits d’accès au contenu protégé {#blacklist-of-application-runtimes-restricted-from-accessing-protected-content}

Spécifie la version du Primetime ou du Flash Runtime qui ne peut pas accéder au contenu. Spécifiez le runtime restreint (Flash Player, AIR ou iOS), la plate-forme et la version.

Exemple de cas d’utilisation : Tout comme la liste noire du client DRM, la dernière version des moteurs d’exécution Flash Player, AIR ou iOS peut être spécifiée comme version minimale requise pour l’acquisition de licence et la lecture de contenu.

Le runtime de l’application peut être identifié par l’un des attributs pris en charge pour les versions client DRM, en plus des attributs suivants :

| **Attribut** | **Valeurs prises en charge** | **Critères de correspondance** | **Description** |
|---|---|---|---|
| Application | &quot;FlashPlayer&quot;, &quot;AIR&quot;, &quot;DRM_Library&quot;, &quot;AVE&quot; | Correspondance exacte | Identifie le nom du runtime de l’application. |


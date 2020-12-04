---
description: La définition de stratégies consiste à définir des conditions pour qu’un utilisateur soit autorisé à lire du contenu vidéo protégé et quand et comment.
seo-description: La définition de stratégies consiste à définir des conditions pour qu’un utilisateur soit autorisé à lire du contenu vidéo protégé et quand et comment.
seo-title: Définition des stratégies
title: Définition des stratégies
uuid: 2d2672ce-5ed4-4868-aa5e-0a9e21a809b3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Définition de stratégies{#setting-policies}

La définition de stratégies consiste à définir des conditions pour qu’un utilisateur soit autorisé à lire du contenu vidéo protégé et quand et comment.

La création de stratégie se produit dans le cadre de votre demande de jeton de licence. (Voir [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) pour un exemple d’utilisation de Widevine).

Une fois que le code côté serveur d&#39;un client a déterminé qu&#39;il délivrera une licence (en fonction des vérifications de droits, de la géolocalisation ou de toute autre information requise), il demande un jeton et *dans le jeton* il spécifie les `securityLevel`, `hdcpOutputControl` et `licenseDuration` requis. Ce sont les options côté client pour une politique Widevine. D&#39;autres solutions DRM offre des approches similaires, mais les détails sont différents dans chaque cas et sont détaillés dans les différents workflows.

>[!NOTE]
>
>Adobe fournit un exemple de serveur de référence qui indique comment implémenter votre propre serveur de droits / vitrine : [Serveur de référence : Exemple de serveur de droits ExpressPlay (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)


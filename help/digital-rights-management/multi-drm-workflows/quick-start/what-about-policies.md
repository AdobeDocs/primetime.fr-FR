---
description: La définition de stratégies est le processus de spécification de conditions pour quand et comment un utilisateur est autorisé à lire du contenu vidéo protégé.
title: Définition des stratégies
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Définition des stratégies{#setting-policies}

La définition de stratégies est le processus de spécification de conditions pour quand et comment un utilisateur est autorisé à lire du contenu vidéo protégé.

La création d’une stratégie s’effectue dans le cadre de votre demande de jeton de licence. (Voir [https://www.expressplay.com/developer/restapi/#widevine-license-token-request](https://www.expressplay.com/developer/restapi/#widevine-license-token-request) par exemple avec Widevine).

Une fois que le code côté serveur d’un client a déterminé qu’il va émettre une licence (en fonction des contrôles des droits, de la géolocalisation ou de toute autre information requise), il demande un jeton, et *dans le jeton* il spécifie les `securityLevel`, `hdcpOutputControl`, et `licenseDuration`. Il s’agit des options côté client pour une stratégie Windows. D&#39;autres solutions DRM proposent des approches similaires, mais les détails sont différents dans chaque cas et sont détaillés dans les différents workflows.

>[!NOTE]
>
>Adobe fournit un exemple de serveur de référence qui indique comment mettre en oeuvre votre propre serveur de droits/storefront : [Serveur de référence : exemple de serveur de droits ExpressPlay (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

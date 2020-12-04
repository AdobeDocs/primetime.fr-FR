---
seo-title: Présentation des abeilles
title: Présentation des abeilles
uuid: c6ee7528-fdfa-4a56-bea2-a5e2dab6d428
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Présentation des abeilles{#bees-overview}

Vous pouvez mettre en oeuvre un service de droits dorsaux (BEES) afin de fournir des droits personnalisés pour votre opération DRM Primetime Cloud.

Par défaut, Primetime Cloud DRM utilise la diffusion de licence anonyme. Cela signifie que toutes les demandes de licence envoyées à Primetime Cloud DRM retourneront une licence valide sans effectuer de vérifications d’authentification/d’autorisation supplémentaires (sauf si vous avez appliqué une contrainte de stratégie qui appelle à l’utilisation de l’authentification Adobe Primetime).

La demande de licence contient la stratégie DRM utilisée lors de l’emballage/chiffrement du contenu. La stratégie DRM est utilisée pour générer la licence DRM renvoyée au client. Dans le scénario par défaut, vous devez prendre toutes les décisions de stratégie DRM au moment de la création du pack de contenu. Les clients qui souhaitent un meilleur contrôle sur ces workflows disposent des options suivantes :

1. Intégrez l’authentification Primetime pour ajouter des vérifications de droits supplémentaires avant la lecture.
1. Créez un service de droits sur site que Primetime Cloud DRM requête avant d’autoriser tout périphérique à lire le contenu que vous avez compressé.

Votre service de droits sur site doit fournir une réponse à Primetime Cloud DRM qui comprend les deux éléments de données suivants :

* `isAllowed`
* `drmPolicyToUse`

Ils déterminent si un périphérique est autorisé à lire le contenu et quelle stratégie DRM utiliser pour générer la licence DRM (si `isAllowed` est vraie).

Ce document porte sur ce que vous devez faire pour réaliser l&#39;option 2 ci-dessus : Mettez en oeuvre votre propre service de droits externe sur site et rendez-le accessible à Primetime Cloud DRM pour le contenu que vous avez compressé.

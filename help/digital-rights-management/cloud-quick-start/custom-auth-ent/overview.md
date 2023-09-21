---
title: Présentation des abeilles
description: Présentation des abeilles
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Présentation des abeilles{#bees-overview}

Vous pouvez mettre en oeuvre un service de droit principal (BEES) afin de fournir des droits personnalisés pour votre opération DRM Primetime Cloud.

Primetime Cloud DRM utilise par défaut la livraison anonyme de licences. Cela signifie que toutes les demandes de licence envoyées à Primetime Cloud DRM renverront une licence valide sans effectuer de vérification d’authentification/d’autorisation supplémentaire (sauf si vous avez appliqué une contrainte de stratégie qui appelle à l’utilisation de l’authentification Adobe Primetime).

La demande de licence contient la stratégie DRM utilisée lors du conditionnement/cryptage du contenu. La stratégie DRM est utilisée pour générer la licence DRM renvoyée au client. Dans le scénario par défaut, vous devez prendre toutes les décisions de stratégie DRM au moment du conditionnement du contenu. Les clients qui souhaitent un meilleur contrôle sur ces workflows disposent des options suivantes :

1. Intégrez l’authentification Primetime pour ajouter des vérifications de droits supplémentaires avant la lecture.
1. Créez un service de droits sur site que Primetime Cloud DRM interrogera avant d’autoriser tout appareil à lire le contenu que vous avez mis en package.

Votre service de droits sur site doit fournir une réponse à Primetime Cloud DRM qui comprend les deux éléments de données suivants :

* `isAllowed`
* `drmPolicyToUse`

Ils déterminent si un appareil est autorisé à lire le contenu, et quelle stratégie DRM utiliser pour générer la licence DRM (si `isAllowed` est vrai).

Ce document couvre ce que vous devez faire pour réaliser l’option 2 ci-dessus : mettre en oeuvre votre propre service de droits externe sur site et le mettre à la disposition de Primetime Cloud DRM pour le contenu que vous avez mis en package.

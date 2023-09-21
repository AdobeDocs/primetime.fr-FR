---
description: Les principaux composants de Primetime DRM sont constitués d’un SDK Java et des environnements d’exécution client Flash Player et Adobe AIR.
title: SDK Java, Flash Player et client Adobe AIR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# SDK ADOBE PRIMETIME DRM {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM est fourni sous la forme d’un SDK Java qui fournit les blocs de création à partir desquels vous pouvez créer une mise en oeuvre de serveur. À l’aide du SDK, vous pouvez créer une solution DRM Primetime adaptée au modèle d’entreprise de votre entreprise.

Les API Java fournies dans le SDK sont décrites dans les sous-sections suivantes.

## API Java pour la gestion des domaines de groupe d’appareils{#java-apis-for-managing-device-group-domains}

Ces API sont utilisées pour permettre au serveur de gérer les demandes de clients pour joindre et quitter les domaines des groupes d’appareils.

Un domaine de groupe d’appareils est un ensemble logique d’appareils qui peuvent partager des licences entre eux. Pour ce faire, chaque appareil doit d’abord rejoindre/s’enregistrer sur le même domaine. Le SDK DRM Primetime, exécuté sur un serveur, doit traiter les demandes de jointure (enregistrement) du domaine du périphérique, ainsi que les demandes de désinscription (désinscription) du domaine du périphérique. Les appareils qui ne sont associés à aucun domaine recevront des licences liées à cet appareil, qui ne peuvent être partagées avec aucun autre appareil.

## API Java pour la protection du contenu{#java-apis-for-protecting-content}

Ces API sont utilisées pour définir des droits et préparer le contenu pour la distribution. Les API de protection du contenu sont les suivantes :

* Gestion des stratégies

  L’API de gestion des stratégies permet de créer et de modifier des stratégies à appliquer au contenu. Les stratégies peuvent être créées ou mises à jour, notamment pour obtenir/définir toutes les règles d’utilisation et autoriser des paramètres supplémentaires dans un espace de noms personnalisé.

* Compilation de contenu

  L’API de package de contenu est utilisée pour chiffrer le contenu et récupérer les métadonnées du contenu empaqueté.

## API Java pour la délivrance de licences{#java-apis-for-issuing-licenses}

Ces API sont utilisées lorsqu’un client demande une licence au serveur. Le SDK prend en charge les requêtes suivantes du client :

* Authentification

  L’API d’authentification peut être utilisée pour gérer les demandes d’authentification et générer des jetons d’authentification.

* Génération et acquisition de licences

  L’API de génération et d’acquisition de licences est utilisée pour générer une licence pour l’utilisateur.

* Prise en charge des clients et du contenu Adobe AIR version 1.5

  À des fins de compatibilité descendante, le SDK dispose d’API pour traiter les demandes provenant d’applications AIR créées pour une utilisation avec AIR version 1.5 et les clients antérieurs et le contenu protégé.

## Implémentation de référence {#reference-implementation}

Le SDK comprend une implémentation de référence, un déploiement DRM Adobe Primetime simple qui explique comment utiliser les API Java. La mise en oeuvre de référence fournit un serveur de licences, un Watched Folder Packager, une application Primetime DRM Manager AIR et des outils de ligne de commande pour le package de contenu et la gestion des stratégies basés sur les API Java. Pour en savoir plus sur l’implémentation de référence DRM Primetime, voir Protection du contenu.

---
description: Les principaux composants de Primetime DRM se composent d’un SDK Java et des environnements d’exécution du client Flash Player et Adobe AIR.
seo-description: Les principaux composants de Primetime DRM se composent d’un SDK Java et des environnements d’exécution du client Flash Player et Adobe AIR.
seo-title: SDK Java, Flash Player et client Adobe AIR
title: SDK Java, Flash Player et client Adobe AIR
uuid: e6daed27-3803-4ef7-ba25-4a180af7502f
translation-type: tm+mt
source-git-commit: ''

---


# Adobe Primetime DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM est fourni en tant que SDK Java qui fournit les blocs de construction à partir desquels vous pouvez créer une mise en oeuvre serveur. Le SDK vous permet de créer une solution DRM Primetime adaptée au modèle d’entreprise de votre entreprise.

Les API Java fournies dans le SDK sont décrites dans les sous-sections suivantes.

## API Java pour la gestion des domaines de groupes de périphériques{#java-apis-for-managing-device-group-domains}

Ces API permettent au serveur de traiter les demandes des clients pour rejoindre et quitter les domaines de groupes de périphériques.

Un domaine de groupe de périphériques est un ensemble logique de périphériques capables de partager des licences entre eux. Pour ce faire, chaque périphérique doit d&#39;abord s&#39;inscrire au même domaine. Le SDK DRM Primetime, exécuté sur un serveur, doit traiter les demandes de jointure (inscription) de domaine de périphérique, ainsi que les demandes de désinscription (désinscription) de domaine de périphérique. Les périphériques qui ne sont associés à aucun domaine recevront des licences liées à ce périphérique, qui ne peut être partagé sur aucun autre périphérique.

## API Java pour la protection du contenu{#java-apis-for-protecting-content}

Ces API sont utilisées pour définir des droits et préparer le contenu pour la distribution. Les API de protection du contenu sont les suivantes :

* Gestion des stratégies

   L’API de gestion des stratégies permet de créer et de modifier des stratégies à appliquer au contenu. Il est possible de créer ou de mettre à jour des stratégies, notamment d’obtenir/de définir toutes les règles d’utilisation et d’autoriser des paramètres supplémentaires dans un espace de nommage personnalisé.

* Emballage de contenu

   L’API de création de package de contenu est utilisée pour chiffrer le contenu et récupérer les métadonnées du contenu assemblé.

## API Java pour la délivrance de licences{#java-apis-for-issuing-licenses}

Ces API sont utilisées lorsqu’un client demande une licence au serveur. Le SDK prend en charge les requêtes suivantes du client :

* Authentification

   L’API d’authentification peut être utilisée pour traiter les demandes d’authentification et générer des jetons d’authentification.

* Génération et acquisition de licences

   L’API de génération et d’acquisition de licences permet de générer une licence pour l’utilisateur.

* Prise en charge des clients et du contenu Adobe AIR version 1.5

   Pour des raisons de compatibilité descendante, le SDK dispose d’API pour traiter les requêtes provenant d’applications AIR créées pour être utilisées avec les clients AIR version 1.5 et versions antérieures et le contenu protégé.

## Implémentation de référence {#reference-implementation}

Le SDK comprend une implémentation de référence, un simple déploiement d’Adobe Primetime DRM qui montre comment utiliser les API Java. L’implémentation de référence fournit un serveur License Server, Watched Folder Packager, l’application AIR de Primetime DRM Manager, ainsi que des outils de ligne de commande pour la gestion des packages de contenu et des stratégies en fonction des API Java. Pour en savoir plus sur l’implémentation de référence DRM Primetime, voir Protection du contenu.
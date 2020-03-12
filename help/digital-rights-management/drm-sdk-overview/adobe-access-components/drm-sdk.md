---
description: Les principaux composants de Primetime DRM sont constitués d’un SDK Java, ainsi que du moteur d’exécution du client Flash Player et Adobe AIR  du.
seo-description: Les principaux composants de Primetime DRM sont constitués d’un SDK Java, ainsi que du moteur d’exécution du client Flash Player et Adobe AIR  du.
seo-title: SDK Java, Flash Player et client Adobe AIR
title: SDK Java, Flash Player et client Adobe AIR
uuid: e6daed27-3803-4ef7-ba25-4a180af7502f
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM est fourni sous la forme d’un SDK Java qui fournit les blocs de création à partir desquels vous pouvez créer une implémentation serveur. Le kit SDK vous permet de créer une solution DRM Primetime adaptée au modèle d’entreprise de votre entreprise.

Les API Java fournies dans le SDK sont décrites dans les sous-sections suivantes.

## API Java pour la gestion des domaines de groupes de périphériques{#java-apis-for-managing-device-group-domains}

Ces API permettent au serveur de traiter les demandes des clients pour rejoindre et quitter des domaines de groupe de périphériques.

Un domaine de groupe de périphériques est un ensemble logique de périphériques capables de partager des licences entre eux. Pour ce faire, chaque périphérique doit d’abord rejoindre/s’enregistrer sur le même domaine. Le SDK DRM Primetime, exécuté sur un serveur, doit traiter les demandes de jointure (inscription) de domaine de périphérique, ainsi que les demandes de désinscription (désinscription) de domaine de périphérique. Les périphériques qui ne sont associés à aucun domaine recevront des licences liées à ce périphérique, qui ne peut être partagé sur aucun autre périphérique.

## API Java pour la protection du contenu{#java-apis-for-protecting-content}

Ces API sont utilisées pour définir des droits et préparer le contenu pour la distribution. Les API de protection du contenu sont les suivantes :

* Gestion des stratégies

   L’API de gestion des stratégies permet de créer et de modifier des stratégies à appliquer au contenu. Les stratégies peuvent être créées ou mises à jour, y compris l’obtention/la définition de toutes les règles d’utilisation et l’autorisation de paramètres supplémentaires dans un  de  personnalisé.

* Assemblage de contenu

   L’API d’assemblage de contenu permet de chiffrer le contenu et de récupérer les métadonnées du contenu assemblé.

## API Java pour la délivrance de licences{#java-apis-for-issuing-licenses}

Ces API sont utilisées lorsqu’un client demande une licence au serveur. Le SDK prend en charge les requêtes suivantes du client :

* Authentification

   L’API d’authentification peut être utilisée pour traiter les demandes d’authentification et générer des jetons d’authentification.

* Génération et acquisition de licences

   L’API de génération et d’acquisition de licences est utilisée pour générer une licence pour l’utilisateur.

* Prise en charge des clients et du contenu Adobe AIR version 1.5

   Pour des raisons de compatibilité descendante, le SDK dispose d’API pour traiter les demandes provenant d’applications AIR créées pour une utilisation avec des clients AIR versions 1.5 et antérieures et du contenu protégé.

## Implémentation de référence {#reference-implementation}

Le SDK comprend une implémentation de référence, un déploiement DRM Adobe Primetime simple qui montre comment utiliser les API Java. L’implémentation de référence fournit un serveur de licences, Watched Folder Packager, l’application AIR de Primetime DRM Manager, ainsi que des outils de ligne de commande pour la création de packages de contenu et la gestion des stratégies en fonction des API Java. Pour en savoir plus sur l’implémentation de référence DRM Primetime, voir Protection du contenu.
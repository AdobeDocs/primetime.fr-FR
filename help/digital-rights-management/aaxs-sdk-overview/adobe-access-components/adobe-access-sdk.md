---
description: Les principaux composants d'Adobe Access sont un SDK Java et les environnements d'exécution du client Flash Player et Adobe AIR.
seo-description: Les principaux composants d'Adobe Access sont un SDK Java et les environnements d'exécution du client Flash Player et Adobe AIR.
seo-title: SDK Java, Flash Player et client Adobe AIR
title: SDK Java, Flash Player et client Adobe AIR
uuid: 6b6c5aa2-56ee-4476-a05b-dcbbe3b9001e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Composants Adobe Access{#adobe-access-components}

Les principaux composants d&#39;Adobe Access sont un SDK Java et les environnements d&#39;exécution du client Flash Player et Adobe AIR.

Pour plus d’informations sur la configuration du SDK, voir Configuration du SDK dans *Utilisation du SDK Adobe Access pour la protection du contenu.*

Le SDK Adobe Access vous permet de développer une solution de gestion des droits numériques qui s’intègre à l’infrastructure métier existante de votre entreprise, telle que les systèmes de gestion de contenu, de facturation et de contrôle d&#39;accès utilisateur. Flash Player et Adobe AIR vous permettent de créer et de déployer facilement des applications grâce auxquelles les utilisateurs peuvent accéder et vue à de grandes bibliothèques de contenu numérique.

## SDK Adobe Access {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Access est fourni sous la forme d’un SDK Java qui fournit les blocs de création à partir desquels vous pouvez créer une mise en oeuvre serveur. Le kit SDK permet de créer une solution Adobe Access adaptée au modèle d’entreprise de votre entreprise.

Les API Java fournies dans le SDK sont décrites dans les sous-sections suivantes.

## API Java pour la gestion des domaines de groupes de périphériques {#java-apis-for-managing-device-group-domains}

Ces API permettent au serveur de traiter les demandes des clients pour rejoindre et quitter les domaines de groupes de périphériques.

Un domaine de groupe de périphériques est un ensemble logique de périphériques capables de partager des licences entre eux. Pour ce faire, chaque périphérique doit d&#39;abord s&#39;inscrire au même domaine. Le SDK Adobe Access, exécuté sur un serveur, doit traiter les demandes de jonction de domaine de périphérique (inscription), ainsi que les demandes de sortie de domaine de périphérique (désinscription). Les périphériques qui ne sont associés à aucun domaine recevront des licences liées à ce périphérique, qui ne peut être partagé sur aucun autre périphérique.

## API Java pour la protection du contenu {#java-apis-for-protecting-content}

Ces API sont utilisées pour définir des droits et préparer le contenu pour la distribution. Les API de protection du contenu sont les suivantes :

* Gestion des stratégies

   L’API de gestion des stratégies permet de créer et de modifier des stratégies à appliquer au contenu. Il est possible de créer ou de mettre à jour des stratégies, notamment d’obtenir/de définir toutes les règles d’utilisation et d’autoriser des paramètres supplémentaires dans un espace de nommage personnalisé.

* Emballage de contenu

   L’API de création de package de contenu est utilisée pour chiffrer le contenu et récupérer les métadonnées du contenu assemblé.

## API Java pour la délivrance de licences {#java-apis-for-issuing-licenses}

Ces API sont utilisées lorsqu’un client demande une licence au serveur. Le SDK prend en charge les requêtes suivantes du client :

* Authentification

   L’API d’authentification peut être utilisée pour traiter les demandes d’authentification et générer des jetons d’authentification.

* Génération et acquisition de licences

   L’API de génération et d’acquisition de licences permet de générer une licence pour l’utilisateur.

* Prise en charge des clients et du contenu Adobe AIR version 1.5

   Pour des raisons de compatibilité descendante, le SDK dispose d’API pour traiter les requêtes provenant d’applications AIR créées pour être utilisées avec les clients AIR version 1.5 et versions antérieures et le contenu protégé.

## Implémentation de référence {#reference-implementation}

Le SDK comprend une implémentation de référence, un déploiement simple d’Adobe Access qui explique comment utiliser les API Java. L’implémentation de référence fournit un serveur License Server, Watched Folder Packager, l’application AIR d’Adobe Access Manager et des outils de ligne de commande pour la gestion des packages de contenu et des stratégies en fonction des API Java. Pour en savoir plus sur l’implémentation des références Adobe Access, voir *Protection du contenu*.

## Adobe Access Server for Protected Streaming {#adobe-access-server-for-protected-streaming}

Pour les cas d’utilisation de la diffusion en flux continu où le contenu est protégé par Adobe Access, par exemple pour la diffusion en flux continu dynamique HTTP Adobe, le logiciel inclut également Adobe Access Server for Protected Streaming. Cette solution peut être facilement déployée sur un conteneur de servlet tel que Tomcat et peut atteindre un haut niveau d&#39;évolutivité et de performances pour répondre aux besoins les plus importants en matière de distribution de contenu.

## Adobe Flash Player {#adobe-flash-player}

Flash Player est un plug-in et un runtime de navigateur léger qui offre aux utilisateurs une expérience cohérente et attrayante, une lecture audio/vidéo étonnante et une portée omniprésente. Flash Player permet une lecture de haute qualité du contenu vidéo téléchargé ou en flux continu. Pour les éditeurs de contenu, Flash Player permet de personnaliser les écrans de lecture entourant le contenu, ce qui permet d’approfondir les expériences de personnalisation de la marque et de les monétiser grâce à la publicité à l’aide de bannières et d’incrustations. Pour les utilisateurs, Flash Player offre une méthode intuitive et visuellement attrayante pour vue du contenu vidéo.

Pour plus d&#39;informations sur Flash Player, consultez : [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR est un environnement d’exécution inter-systèmes d’exploitation qui permet aux producteurs de contenu d’étendre leurs investissements existants sur le Web à l’ordinateur de bureau en concevant des applications multimédia personnalisées. Basé sur des technologies éprouvées et ouvertes, il offre aux entreprises un moyen fiable et simplifié de développer et de déployer des applications personnalisées qui peuvent être fiables pour offrir une expérience utilisateur plus sûre et plus agréable. Adobe AIR permet aux entreprises d’intégrer facilement des médias enrichis afin de créer une expérience utilisateur plus immersive et interactive. Il permet aux développeurs d’utiliser des outils familiers tels que des logiciels HTML, JavaScript, Flash ou Adobe® Flex® pour déployer leur combinaison unique d’applications Internet enrichies sur Windows, Macintosh ou Linux.

Les entreprises ont un contrôle total sur l&#39;interface utilisateur et peuvent concevoir une expérience utilisateur pour refléter et renforcer leur marque. Grâce à la prise en charge intégrée de la lecture de contenu protégé par le SDK Adobe Access, Adobe AIR permet de créer des chaînes de distribution de contenu personnalisées de bout en bout.

Pour plus d’informations sur Adobe AIR, voir : [www.adobe.com/go/air](https://www.adobe.com/go/air)

## Applications iOS et Android natives {#native-ios-and-android-applications}

Applications iOS et Android natives Disponibles uniquement pour les clients Adobe Primetime, Adobe Access DRM 4.0 et versions ultérieures peut être utilisé pour protéger les vidéos utilisées dans les applications natives (non Flash) sur les périphériques mobiles. Pour qu’une application utilise ce contenu protégé, elle doit être implémentée à l’aide des bibliothèques clientes Adobe Primetime.

Pour plus d’informations sur Adobe Primetime, consultez : [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)
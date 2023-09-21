---
description: Les principaux composants d’Adobe Access sont constitués d’un SDK Java et des environnements d’exécution client Flash Player et Adobe AIR.
title: SDK Java, Flash Player et client Adobe AIR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Composants Accès aux Adobes{#adobe-access-components}

Les principaux composants d’Adobe Access sont constitués d’un SDK Java et des environnements d’exécution client Flash Player et Adobe AIR.

Pour plus d’informations sur la configuration du SDK, voir Configuration du SDK dans *Utilisation du SDK Adobe Access pour la protection du contenu.*

Le SDK Adobe Access vous permet de développer une solution de gestion des droits numériques qui s’intègre à l’infrastructure commerciale existante de votre entreprise, telle que la gestion de contenu, la facturation et les systèmes de contrôle d’accès des utilisateurs. Flash Player et Adobe AIR vous permettent de créer et de déployer facilement des applications permettant aux consommateurs d’accéder à de grandes bibliothèques de contenu numérique et de les afficher.

## Adobe Access SDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Access est fourni sous la forme d’un SDK Java qui fournit les blocs de création à partir desquels vous pouvez créer une mise en oeuvre de serveur. À l’aide du SDK, vous pouvez créer une solution Adobe Access adaptée au modèle d’entreprise de votre entreprise.

Les API Java fournies dans le SDK sont décrites dans les sous-sections suivantes.

## API Java pour la gestion des domaines de groupe d’appareils {#java-apis-for-managing-device-group-domains}

Ces API sont utilisées pour permettre au serveur de gérer les demandes de clients pour joindre et quitter les domaines des groupes d’appareils.

Un domaine de groupe d’appareils est un ensemble logique d’appareils qui peuvent partager des licences entre eux. Pour ce faire, chaque appareil doit d’abord rejoindre/s’enregistrer sur le même domaine. Le SDK Adobe Access, exécuté sur un serveur, doit traiter les demandes de jointure (enregistrement) sur le domaine du périphérique, ainsi que les demandes de désinscription (désinscription) sur le domaine du périphérique. Les appareils qui ne sont associés à aucun domaine recevront des licences liées à cet appareil, qui ne peuvent être partagées avec aucun autre appareil.

## API Java pour la protection du contenu {#java-apis-for-protecting-content}

Ces API sont utilisées pour définir des droits et préparer le contenu pour la distribution. Les API de protection du contenu sont les suivantes :

* Gestion des stratégies

  L’API de gestion des stratégies permet de créer et de modifier des stratégies à appliquer au contenu. Les stratégies peuvent être créées ou mises à jour, notamment pour obtenir/définir toutes les règles d’utilisation et autoriser des paramètres supplémentaires dans un espace de noms personnalisé.

* Compilation de contenu

  L’API de package de contenu est utilisée pour chiffrer le contenu et récupérer les métadonnées du contenu empaqueté.

## API Java pour la délivrance de licences {#java-apis-for-issuing-licenses}

Ces API sont utilisées lorsqu’un client demande une licence au serveur. Le SDK prend en charge les requêtes suivantes du client :

* Authentification

  L’API d’authentification peut être utilisée pour gérer les demandes d’authentification et générer des jetons d’authentification.

* Génération et acquisition de licences

  L’API de génération et d’acquisition de licences est utilisée pour générer une licence pour l’utilisateur.

* Prise en charge des clients et du contenu Adobe AIR version 1.5

  À des fins de compatibilité descendante, le SDK dispose d’API pour traiter les demandes provenant d’applications AIR créées pour une utilisation avec AIR version 1.5 et les clients antérieurs et le contenu protégé.

## Implémentation de référence {#reference-implementation}

Le SDK comprend une implémentation de référence, un déploiement simple d’accès aux Adobes qui explique comment utiliser les API Java. La mise en oeuvre de référence fournit un serveur de licences, un gestionnaire de dossiers de contrôle, une application AIR Adobe Access Manager et des outils de ligne de commande pour le conditionnement de contenu et la gestion des stratégies en fonction des API Java. Pour en savoir plus sur l’implémentation de la référence d’accès aux Adobes, voir *Protection du contenu*.

## Adobe Access Server pour la diffusion en continu protégée {#adobe-access-server-for-protected-streaming}

Pour les cas d’utilisation de diffusion en continu où le contenu est protégé par l’accès à l’Adobe, par exemple pour le HTTP Dynamic Streaming par Adobe, le logiciel inclut également Adobe Access Server for Protected Streaming. Cette solution peut être facilement déployée sur un conteneur de servlets tel que Tomcat et peut atteindre un haut niveau d’évolutivité et de performance pour répondre aux besoins les plus importants en matière de distribution de contenu.

## Flash Player Adobe {#adobe-flash-player}

Flash Player est un module complémentaire et un composant d’exécution léger du navigateur qui offre des expériences utilisateur cohérentes et attrayantes, une lecture audio/vidéo étonnante et une portée omniprésente. Flash Player offre une lecture de haute qualité du contenu vidéo téléchargé ou en flux continu. Pour les éditeurs de contenu, Flash Player fournit les moyens de personnaliser les écrans de lecture entourant le contenu, ce qui permet d’offrir des expériences de valorisation de marque plus approfondies et une monétisation par le biais de la publicité à l’aide de bannières et de superpositions. Pour les consommateurs, Flash Player offre une méthode intuitive et visuellement attrayante d’affichage du contenu vidéo.

Pour plus d’informations sur le Flash Player, rendez-vous sur : [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR est un composant d’exécution de plusieurs systèmes d’exploitation qui permet aux producteurs de contenu d’étendre leurs investissements existants dans le web au bureau en concevant des applications multimédia personnalisées. Basé sur des technologies ouvertes et éprouvées, il offre un moyen fiable et simplifié aux entreprises de développer et déployer des applications personnalisées fiables pour offrir une expérience utilisateur plus sécurisée et plus agréable. Adobe AIR permet aux entreprises d’intégrer facilement des médias enrichis afin de créer une expérience utilisateur plus immersive et interactive. Il permet aux développeurs d’utiliser des outils familiers tels que des logiciels HTML, JavaScript, Flash ou Adobe® Flex® pour déployer leur combinaison unique d’applications Internet riches sous Windows, Macintosh ou Linux.

Les entreprises contrôlent entièrement l’interface utilisateur et peuvent concevoir une expérience utilisateur qui reflète et renforce leur marque. Grâce à la prise en charge intégrée de la lecture du contenu protégé par le SDK Adobe Access, Adobe AIR permet de créer des chaînes de distribution de contenu de bout en bout personnalisées.

## Applications iOS et Android natives {#native-ios-and-android-applications}

Applications iOS et Android natives Disponibles uniquement pour les clients Adobe Primetime, Adobe Access DRM 4.0 et versions ultérieures peut être utilisé pour protéger la vidéo consommée dans les applications natives (non Flashs) sur les appareils mobiles. Pour qu’une application utilise ce contenu protégé, elle doit être implémentée à l’aide des bibliothèques clientes Adobe Primetime.

Pour plus d’informations sur Adobe Primetime, rendez-vous sur : [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)

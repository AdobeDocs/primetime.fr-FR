---
description: Les principaux composants d’Adobe Access sont un SDK Java, ainsi que le moteur d’exécution du client Flash Player et Adobe AIR  .
seo-description: Les principaux composants d’Adobe Access sont un SDK Java, ainsi que le moteur d’exécution du client Flash Player et Adobe AIR  .
seo-title: SDK Java, Flash Player et client Adobe AIR
title: SDK Java, Flash Player et client Adobe AIR
uuid: 6b6c5aa2-56ee-4476-a05b-dcbbe3b9001e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Composants Adobe Access{#adobe-access-components}

Les principaux composants d’Adobe Access sont un SDK Java, ainsi que le moteur d’exécution du client Flash Player et Adobe AIR  .

Pour plus d’informations sur la configuration du SDK, voir Configuration du SDK dans *Utilisation du SDK Adobe Access pour la protection du contenu.*

Le kit SDK Adobe Access vous permet de développer une solution de gestion des droits numériques qui s’intègre à l’infrastructure opérationnelle existante de votre entreprise, telle que les systèmes de , de facturation et de  des utilisateur. Flash Player et Adobe AIR vous permettent de créer et de déployer facilement des applications permettant aux utilisateurs d’accéder à de grandes bibliothèques de contenu numérique et de les  à travers ces applications.

## SDK Adobe Access {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Access est fourni sous la forme d’un SDK Java qui fournit les blocs de création à partir desquels vous pouvez créer une mise en oeuvre serveur. Le kit SDK vous permet de créer une solution Adobe Access adaptée au modèle d’entreprise de votre entreprise.

Les API Java fournies dans le SDK sont décrites dans les sous-sections suivantes.

## API Java pour la gestion des domaines de groupes de périphériques {#java-apis-for-managing-device-group-domains}

Ces API permettent au serveur de traiter les demandes des clients pour rejoindre et quitter des domaines de groupe de périphériques.

Un domaine de groupe de périphériques est un ensemble logique de périphériques capables de partager des licences entre eux. Pour ce faire, chaque périphérique doit d’abord rejoindre/s’enregistrer sur le même domaine. Le SDK Adobe Access, exécuté sur un serveur, doit traiter les demandes de jonction (inscription) de domaine de périphérique, ainsi que les demandes de désinscription (désinscription) de domaine de périphérique. Les périphériques qui ne sont associés à aucun domaine recevront des licences liées à ce périphérique, qui ne peut être partagé sur aucun autre périphérique.

## API Java pour la protection du contenu {#java-apis-for-protecting-content}

Ces API sont utilisées pour définir des droits et préparer le contenu pour la distribution. Les API de protection du contenu sont les suivantes :

* Gestion des stratégies

   L’API de gestion des stratégies permet de créer et de modifier des stratégies à appliquer au contenu. Les stratégies peuvent être créées ou mises à jour, y compris l’obtention/la définition de toutes les règles d’utilisation et l’autorisation de paramètres supplémentaires dans un  de  personnalisé.

* Assemblage de contenu

   L’API d’assemblage de contenu permet de chiffrer le contenu et de récupérer les métadonnées du contenu assemblé.

## API Java pour la délivrance de licences {#java-apis-for-issuing-licenses}

Ces API sont utilisées lorsqu’un client demande une licence au serveur. Le SDK prend en charge les requêtes suivantes du client :

* Authentification

   L’API d’authentification peut être utilisée pour traiter les demandes d’authentification et générer des jetons d’authentification.

* Génération et acquisition de licences

   L’API de génération et d’acquisition de licences est utilisée pour générer une licence pour l’utilisateur.

* Prise en charge des clients et du contenu Adobe AIR version 1.5

   Pour des raisons de compatibilité descendante, le SDK dispose d’API pour traiter les demandes provenant d’applications AIR créées pour une utilisation avec des clients AIR versions 1.5 et antérieures et du contenu protégé.

## Implémentation de référence {#reference-implementation}

Le SDK comprend une implémentation de référence, un déploiement simple d’Adobe Access qui montre comment utiliser les API Java. L’implémentation de référence fournit un serveur de licences, Watched Folder Packager, l’application AIR d’Adobe Access Manager et des outils de ligne de commande pour la création de packages de contenu et la gestion des stratégies en fonction des API Java. Pour en savoir plus sur l’implémentation des références Adobe Access, voir *Protection du contenu*.

## Adobe Access Server for Protected Streaming {#adobe-access-server-for-protected-streaming}

Pour les cas d’utilisation de diffusion en flux continu où le contenu est protégé par Adobe Access, comme pour la diffusion en flux continu dynamique HTTP Adobe, le logiciel inclut également Adobe Access Server for Protected Streaming. Cette solution peut être facilement déployée sur un de servlets tel que Tomcat et peut atteindre un haut niveau d’évolutivité et de performances pour répondre aux besoins les plus importants en matière de distribution de contenu.

## Adobe Flash Player {#adobe-flash-player}

Flash Player est un plug-in et un environnement d’exécution de navigateur léger qui offre aux utilisateurs une expérience cohérente et attrayante, une lecture audio/vidéo époustouflante et une portée omniprésente. Flash Player offre une lecture de haute qualité du contenu vidéo en flux continu ou téléchargé. Pour les éditeurs de contenu, Flash Player permet de personnaliser les écrans de lecture entourant le contenu, ce qui permet d’approfondir les expériences de marque et la monétisation par le biais de la publicité à l’aide de bannières et d’incrustations. Pour les consommateurs, Flash Player offre une méthode intuitive et attrayante pour de contenu vidéo.

Pour plus d&#39;informations sur Flash Player, consultez : [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR est un environnement d’exécution inter-systèmes d’exploitation qui permet aux producteurs de contenu d’étendre leurs investissements existants sur le Web à l’ordinateur de bureau en concevant des applications multimédia personnalisées. S&#39;appuyant sur des technologies éprouvées et ouvertes, il offre aux entreprises un moyen fiable et simplifié de développer et de déployer des applications personnalisées qui peuvent être fiables pour offrir une expérience utilisateur plus sûre et plus agréable. Adobe AIR permet aux entreprises d’intégrer facilement des médias enrichis afin de créer une expérience utilisateur plus immersive et interactive. Il permet aux développeurs d’utiliser des outils familiers tels que des logiciels HTML, JavaScript, Flash ou Adobe® Flex® pour déployer leur combinaison unique d’applications Internet enrichies sur Windows, Macintosh ou Linux.

Les entreprises ont un contrôle total de l’interface utilisateur et peuvent concevoir une expérience utilisateur pour refléter et renforcer leur marque. Grâce à la prise en charge intégrée de la lecture de contenu protégé par le kit SDK Adobe Access, Adobe AIR permet de créer des chaînes de distribution de contenu de bout en bout personnalisées.

Pour plus d’informations sur Adobe AIR, voir : [www.adobe.com/go/air](https://www.adobe.com/go/air)

## Applications iOS et Android natives {#native-ios-and-android-applications}

Applications iOS et Android natives Disponibles uniquement pour les clients Adobe Primetime, Adobe Access DRM 4.0 et versions ultérieures peut être utilisé pour protéger la vidéo consommée dans les applications natives (non Flash) sur les périphériques mobiles. Pour qu’une application utilise ce contenu protégé, elle doit être implémentée à l’aide des bibliothèques clientes Adobe Primetime.

Pour plus d’informations sur Adobe Primetime, consultez : [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)
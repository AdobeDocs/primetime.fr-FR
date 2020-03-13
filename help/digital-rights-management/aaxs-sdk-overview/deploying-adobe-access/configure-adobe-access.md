---
seo-title: Déploiement d’Adobe Access
title: Déploiement d’Adobe Access
uuid: 9f9a9931-f607-4b1a-9209-0236a4c197ca
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Déploiement d’Adobe Access {#deploy-adobe-access}

L’un des principaux avantages du SDK Adobe Access est que vous pouvez l’installer sur n’importe quel serveur d’applications Java™ ou de servlets, tel que Tomcat. Vous avez également besoin du JDK™ 1.5 ou version ultérieure. Pour plus d’informations sur la configuration logicielle requise, voir Configuration requise pour le SDK Adobe Access : [: https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Les étapes générales pour déployer Adobe Access sont les suivantes :

1. Installez et configurez le SDK Adobe Access.
1. Obtenez des certificats numériques auprès d’Adobe.
1. Créez un serveur de licences à l’aide du SDK ou déployez Adobe Access Server pour la diffusion en flux continu protégée.
1. Créez un pack de contenu et des outils de gestion des stratégies pour regrouper du contenu, utilisez les outils de préparation de contenu fournis ou concédez une licence à l’un des modules de diffusion en flux continu dynamique HTTP Adobe.
1. Définissez des règles d’utilisation pour votre contenu et créez des stratégies en fonction de ces règles.
1. Mettez en package votre contenu à l’aide des outils de gestion des packages et des stratégies.
1. Développez des applications vidéo avec lesquelles les clients peuvent votre contenu protégé à l’aide de Flash Player ou d’Adobe AIR, ou utilisez une plateforme vidéo en ligne (OVP) établie qui prend en charge Adobe Access.
1. Déployez un fichier SWF en vue de l’utiliser avec Flash Player sur votre site Web ou publiez le programme d’installation d’Adobe AIR pour le télécharger.

Ces étapes sont développées dans les sections suivantes, avec des références à d’autres  de contenant des informations supplémentaires.

## Déploiement sur un système d’exploitation 64 bits {#deploying-on-a-bit-operating-system}

Un système d’exploitation 64 bits, tel que la version 64 bits de RedHat ou de Windows, offre de meilleures performances qu’un système d’exploitation 32 bits.

## Installation du SDK Adobe Access {#install-adobe-access-sdk}

Le SDK Adobe Access est fourni sous la forme d’un fichier d’archive Java (JAR). Pour en savoir plus sur l’installation d’Adobe Access, voir *Utilisation du SDK Adobe Access pour la protection du contenu* et des *directivesde déploiement sécurisé*.

## Mise en oeuvre d’un serveur de licences {#implement-a-license-server}

A l’aide du SDK Adobe Access, vous devez créer un serveur de licences. Lorsque le contenu est protégé à l’aide d’Adobe Access, il ne peut pas être affiché tant qu’une licence n’a pas été délivrée au consommateur par le serveur de licences. Si des licences basées sur l’identité sont utilisées, l’authentification basée sur un mot de passe garantit que seuls les consommateurs autorisés peuvent ouvrir et du contenu.

Lors de la mise en oeuvre d’un serveur de licences, vous devez obtenir les certificats numériques nécessaires auprès d’Adobe. Pour obtenir des instructions détaillées sur la demande de certificats, reportez-vous au d’inscription de certificats Adobe Access.

Pour en savoir plus sur la mise en oeuvre d’un serveur de licences et l’obtention de certificats numériques, voir* Utilisation du SDK Adobe Access pour la protection du contenu.*

## Création d’outils de création de packages de contenu et de gestion des stratégies {#create-content-packaging-and-policy-management-tools}

Le kit SDK Adobe Access vous permet de créer des outils de gestion de contenu et d’assemblage de contenu. Les API de gestion des stratégies permettent aux administrateurs de créer, de  détails et de mettre à jour des stratégies. Les API de création de package incorporent la stratégie dans le fichier FLV ou F4V et chiffrent le fichier à l’aide de la clé de chiffrement de contenu.

Le SDK Adobe Access comprend une implémentation de référence ( [!DNL AdobePackager.jar]) qui fournit des exemples d’outils de gestion de règles et de création de packages de contenu ( [!DNL AdobePolicyManager.jar]).

Pour plus d’informations sur la création d’outils de gestion de package et de stratégie de contenu, voir *Utilisation du SDK Adobe Access pour la protection du contenu*.

## Création de stratégies et de contenu de package {#create-policies-and-package-content}

A l’aide des règles d’utilisation prises en charge par le SDK, vous devez définir et créer des stratégies pour prendre en charge le modèle d’entreprise de votre entreprise, puis assembler votre contenu à l’aide de ces stratégies. Une fois les stratégies appliquées au contenu au cours de l’assemblage, vous pouvez conserver le contrôle de votre contenu, quelle que soit sa diffusion.

Les stratégies d’Adobe Access prennent en charge un large éventail de règles d’utilisation, notamment :

* Spécifier le nombre de jours pendant lesquels une licence est valide lorsqu’un utilisateur commence à regarder le contenu.
* Autorisation de la mise en cache des licences.
* Spécification des environnements d’exécution client et des versions pouvant accéder au contenu (par exemple, les utilisateurs doivent disposer d’une certaine application Adobe AIR ou d’une version spécifique de Flash Player).
* Obliger les consommateurs à s’authentifier à l’aide d’un nom d’utilisateur et d’un mot de passe avant de consulter un contenu protégé ou d’autoriser un accès anonyme.

Pour en savoir plus sur l’assemblage de contenu, voir *Protection du contenu*. Pour en savoir plus sur les règles d’utilisation et les modèles d’entreprise qu’elles prennent en charge, voir Règles *d’* utilisation.

## Développement d’applications pour la lecture vidéo {#develop-applications-for-video-playback}

Pour permettre aux utilisateurs d’accéder au contenu et de le , développez une application de lecture vidéo à l’aide de Flash Player ou d’Adobe AIR. Une fois que vous avez développé une application de lecture vidéo, vous devez la déployer sur les consommateurs. Si vous développez une application à l’aide de Flash Player, hébergez-la sur le site Web de votre entreprise. Si vous développez une application à l’aide d’Adobe® AIR®, publiez le programme d’installation de l’application AIR afin que les utilisateurs puissent télécharger et installer l’application sur leur ordinateur.

Pour en savoir plus sur le développement d’applications de lecture vidéo personnalisées à utiliser avec Adobe Access, consultez le chapitre &quot;Utilisation de vidéos&quot; du Guide [du développeur](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)ActionScript 3.0*, du Centre [de technologie vidéo](https://www.adobe.com/devnet/video/)Adobe et du Cadre multimédia Open Source.
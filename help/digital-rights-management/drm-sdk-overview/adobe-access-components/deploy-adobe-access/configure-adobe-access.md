---
title: Déployer Adobe Primetime DRM
description: Déployer Adobe Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Déployer Adobe Primetime DRM {#configure-adobe-primetime-drm}

L’un des principaux avantages du SDK DRM Adobe Primetime est que vous pouvez l’installer sur n’importe quel serveur d’applications Java™ ou conteneur de servlets, tel que Tomcat. Vous avez également besoin de JDK™ 1.5 ou version ultérieure. Pour plus d’informations sur la configuration logicielle requise, voir Configurations de la plateforme SDK DRM Primetime : [https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Les étapes générales pour déployer Primetime DRM sont les suivantes :

1. Installez et configurez le SDK DRM Primetime.
1. Obtenez des certificats numériques auprès d’Adobe.
1. Créez un serveur de licences à l’aide du SDK ou déployez Primetime DRM Server pour la diffusion en continu protégée.
1. Créez un package de contenu et des outils de gestion de stratégie pour regrouper le contenu, utiliser les outils de préparation de contenu fournis ou accorder une licence à l’un des packages de HTTP Dynamic Streaming d’Adobe.
1. Définissez des règles d’utilisation pour votre contenu, puis créez des stratégies en fonction de ces règles.
1. Regroupez votre contenu à l’aide des outils de gestion des packages et des stratégies.
1. Développez des applications vidéo avec lesquelles les consommateurs peuvent afficher votre contenu protégé à l’aide de Flash Player ou Adobe AIR, ou utilisez une plateforme vidéo en ligne OVP (Online Video Platform) qui prend en charge Primetime DRM.
1. Déployez un fichier de SWF à utiliser avec Flash Player sur votre site web ou publiez le programme d’installation d’Adobe AIR pour téléchargement.

Ces étapes sont décrites plus en détail dans les sections suivantes, avec des références à d’autres documents contenant des informations supplémentaires.

## Déploiement sur un système d’exploitation 64 bits{#deploying-on-a-bit-operating-system}

Un système d’exploitation 64 bits, tel que la version 64 bits de RedHat ou Windows, offre de meilleures performances qu’un système d’exploitation 32 bits.

## Installation du SDK Adobe Primetime DRM {#install-adobe-primetime-drm-sdk}

Le SDK DRM Primetime est fourni sous la forme d’un fichier d’archive Java (JAR). Pour en savoir plus sur l’installation de Primetime DRM, voir Utilisation du SDK DRM Adobe Primetime pour la protection du contenu et des directives de déploiement sécurisé.

## Mise en oeuvre d’un serveur de licences {#implement-a-license-server}

Avec le SDK Adobe Primetime DRM, vous devez créer un serveur de licences. Lorsque le contenu est protégé à l’aide de Primetime DRM, il ne peut pas être affiché tant qu’une licence n’a pas été émise au consommateur par le serveur de licences. Si une licence basée sur l’identité est utilisée, l’authentification par mot de passe garantit que seuls les consommateurs autorisés peuvent ouvrir et afficher du contenu.

Lors de la mise en oeuvre d’un serveur de licences, vous devez obtenir les certificats numériques nécessaires auprès d’Adobe. Pour obtenir des instructions détaillées sur la demande de certificats, reportez-vous au document Inscription de certificat DRM Primetime .

Pour en savoir plus sur la mise en oeuvre d’un serveur de licences et l’obtention de certificats numériques, voir **Utilisation du SDK DRM Adobe Primetime pour la protection du contenu.**

## Créer un package de contenu et des outils de gestion des stratégies{#create-content-packaging-and-policy-management-tools}

A l’aide du SDK Adobe Primetime DRM, vous pouvez créer un package de contenu et des outils de gestion de stratégie. Les API de gestion des stratégies permettent aux administrateurs de créer, d’afficher les détails et de mettre à jour des stratégies. Les API de package intègrent la stratégie dans un fichier vidéo et chiffrent le fichier à l’aide de la clé de chiffrement du contenu.

Le SDK DRM Primetime comprend une mise en oeuvre de référence ( [!DNL AdobePackager.jar]) qui fournit des exemples de conditionnement de contenu et d’outils de gestion de stratégie ( [!DNL AdobePolicyManager.jar]).

Pour en savoir plus sur la création d’un package de contenu et d’outils de gestion des stratégies, voir **Utilisation du SDK Adobe Primetime DRM pour la protection du contenu.**

## Création de stratégies et de contenu de package {#create-policies-and-package-content}

À l’aide des règles d’utilisation prises en charge par le SDK, vous devez définir et créer des stratégies prenant en charge le modèle d’entreprise de votre entreprise, puis regrouper votre contenu à l’aide de ces stratégies. Une fois les stratégies appliquées au contenu lors du conditionnement, vous pouvez contrôler le contenu, quelle que soit la diffusion.

Les stratégies d’Adobe Primetime DRM prennent en charge un large éventail de règles d’utilisation, notamment :

* La spécification du nombre de jours de validité d’une licence lorsqu’un consommateur commence à regarder le contenu.
* Autorisation de la mise en cache des licences.
* Spécification des environnements d’exécution et versions client pouvant accéder au contenu (par exemple, les utilisateurs doivent disposer d’une certaine application Adobe AIR ou d’une version spécifique du Flash Player).
* Obliger les consommateurs à s’authentifier à l’aide d’un nom d’utilisateur et d’un mot de passe avant d’afficher le contenu protégé ou d’autoriser l’accès anonyme.

Pour en savoir plus sur le contenu du package, voir *Protection du contenu*. Pour en savoir plus sur les règles d’utilisation et les modèles d’entreprise qu’elles prennent en charge, voir *Règles d’utilisation*.

## Développement d’applications pour la lecture vidéo {#develop-applications-for-video-playback}

Pour permettre aux consommateurs d’accéder au contenu et de le consulter, développez une application de lecture vidéo à l’aide de Flash Player ou Adobe AIR. Une fois que vous avez développé une application de lecture vidéo, vous devez la déployer sur les consommateurs. Si vous développez une application à l’aide de Flash Player, hébergez-la sur le site web de votre entreprise. Si vous développez une application à l’aide d’Adobe® AIR®, publiez le programme d’installation de l’application AIR afin que les clients puissent télécharger et installer l’application sur leur ordinateur.

Pour en savoir plus sur le développement d’applications de lecture vidéo personnalisées à utiliser avec Adobe Primetime DRM, reportez-vous au chapitre &quot;Utilisation de vidéos&quot; dans [Guide du développeur d’ActionScript 3.0](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html), la variable [Centre de technologie vidéo Adobe](https://www.adobe.com/devnet/video/)et le Open Source Media Framework.

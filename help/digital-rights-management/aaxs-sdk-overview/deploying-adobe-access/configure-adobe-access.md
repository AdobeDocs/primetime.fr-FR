---
seo-title: Déploiement de l’accès aux Adobes
title: Déploiement de l’accès aux Adobes
uuid: 9f9a9931-f607-4b1a-9209-0236a4c197ca
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Déployer l&#39;accès à l&#39;Adobe {#deploy-adobe-access}

L’un des principaux avantages du SDK Adobe Access est que vous pouvez l’installer sur n’importe quel serveur d’applications Java™ ou conteneur de servlet, tel que Tomcat. Vous avez également besoin du JDK™ 1.5 ou version ultérieure. Pour plus d’informations sur la configuration logicielle requise, voir Configuration requise pour le SDK d’accès aux Adobes : [ : https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Les étapes générales permettant de déployer Accès aux Adobes sont les suivantes :

1. Installez et configurez le SDK d’accès aux Adobes.
1. Récupérez des certificats numériques à partir d’un Adobe.
1. Créez un serveur de licences à l’aide du SDK ou déployez Adobe Access Server for Protected Streaming.
1. Créez un pack de contenu et des outils de gestion des stratégies pour regrouper du contenu, utiliser les outils de préparation de contenu fournis ou concéder une licence à l’un des Adobes HTTPs Dynamic Streaming.
1. Définissez des règles d’utilisation pour votre contenu et créez des stratégies pour les prendre en charge.
1. Empaquetez votre contenu à l’aide des outils de gestion des packages et des stratégies.
1. Développez des applications vidéo avec lesquelles les utilisateurs peuvent vue votre contenu protégé à l’aide de Flash Player ou de Adobe AIR, ou utilisez une plateforme de vidéo en ligne OVP (Online Video Platform) qui prend en charge l’accès aux Adobes.
1. Déployez un fichier SWF à utiliser avec le Flash Player sur votre site Web ou publiez le programme d’installation Adobe AIR pour le télécharger.

Ces étapes sont décrites plus en détail dans les sections suivantes, avec des références à d&#39;autres documents contenant des informations supplémentaires.

## Déploiement sur un système d’exploitation 64 bits {#deploying-on-a-bit-operating-system}

Un système d&#39;exploitation 64 bits, tel que la version 64 bits de RedHat ou de Windows, offre de bien meilleures performances qu&#39;un système d&#39;exploitation 32 bits.

## Installer le SDK d&#39;accès aux Adobes {#install-adobe-access-sdk}

Adobe Access SDK est fourni sous la forme d’un fichier d’archive Java (JAR). Pour en savoir plus sur l’installation d’Accès aux Adobes, voir *Utilisation du SDK d’accès aux Adobes pour la protection du contenu* et *Secure Deployment Guidelines*.

## Mise en oeuvre d’un serveur de licences {#implement-a-license-server}

A l’aide du SDK d’accès aux Adobes, vous devez créer un serveur de licences. Lorsque le contenu est protégé à l’aide d’Adobe Access, il ne peut pas être affiché tant qu’une licence n’a pas été délivrée au consommateur par le serveur de licences. Si des licences basées sur l’identité sont utilisées, l’authentification basée sur un mot de passe garantit que seuls les utilisateurs autorisés peuvent ouvrir et vue du contenu.

Lors de la mise en oeuvre d’un serveur de licences, vous devez obtenir les certificats numériques nécessaires auprès de l’Adobe. Pour obtenir des instructions détaillées sur la demande de certificats, reportez-vous au document d&#39;inscription de certificat d&#39;accès à l&#39;Adobe.

Pour en savoir plus sur la mise en oeuvre d’un serveur de licences et l’obtention de certificats numériques, voir* Utilisation du SDK d’accès aux Adobes pour la protection du contenu.*

## Création d’un pack de contenu et d’outils de gestion des stratégies {#create-content-packaging-and-policy-management-tools}

A l’aide du SDK Adobe Access, vous pouvez créer un pack de contenu et des outils de gestion des stratégies. Les API de gestion des stratégies permettent aux administrateurs de créer, de vue des détails et de mettre à jour des stratégies. Les API de création de package incorporent la stratégie dans le fichier FLV ou F4V et chiffrent le fichier à l’aide de la clé de chiffrement de contenu.

Le SDK d&#39;accès à l&#39;Adobe comprend une implémentation de référence ( [!DNL AdobePackager.jar]) qui fournit des exemples d&#39;empaquetage du contenu et d&#39;outils de gestion des stratégies ( [!DNL AdobePolicyManager.jar]).

Pour en savoir plus sur la création d’outils d’empaquetage de contenu et de gestion des stratégies, voir *Utilisation du SDK d’accès aux Adobes pour la protection du contenu*.

## Création de stratégies et de contenu de package {#create-policies-and-package-content}

A l’aide des règles d’utilisation prises en charge par le SDK, vous devez définir et créer des stratégies prenant en charge le modèle d’entreprise de votre entreprise, puis regrouper votre contenu à l’aide de ces stratégies. Une fois les stratégies appliquées au contenu lors de la création de packs, vous pouvez contrôler le contenu quelle que soit sa diffusion.

Les stratégies d&#39;accès aux Adobes prennent en charge un large éventail de règles d&#39;utilisation différentes, notamment :

* Spécification du nombre de jours pendant lesquels une licence est valide lorsqu’un utilisateur commence à regarder le contenu.
* Autorisation de la mise en cache des licences.
* Spécification des runtimes et versions client qui peuvent accéder au contenu (par exemple, les utilisateurs doivent disposer d’une certaine application Adobe AIR ou d’une version spécifique du Flash Player).
* Obliger les consommateurs à s’authentifier à l’aide d’un nom d’utilisateur et d’un mot de passe avant d’afficher du contenu protégé ou d’autoriser l’accès anonyme.

Pour en savoir plus sur l’emballage du contenu, voir *Protection du contenu*. Pour en savoir plus sur les règles d’utilisation et les modèles commerciaux qu’elles prennent en charge, voir *Règles d’utilisation*.

## Développement d’applications pour la lecture vidéo {#develop-applications-for-video-playback}

Pour permettre aux consommateurs d’accéder au contenu et de le vue, développez une application de lecture vidéo à l’aide de Flash Player ou de Adobe AIR. Une fois que vous avez développé une application de lecture vidéo, vous devez la déployer auprès des clients. Si vous développez une application à l’aide du Flash Player, hébergez-la sur le site Web de votre entreprise. Si vous développez une application à l’aide d’Adobe® AIR®, publiez le programme d’installation de l’application AIR afin que les utilisateurs puissent télécharger et installer l’application sur leur ordinateur.

Pour en savoir plus sur le développement d’applications de lecture vidéo personnalisées à utiliser avec Adobe Access, consultez le chapitre &quot;Utilisation de la vidéo&quot; du [Guide du développeur ActionScript 3.0](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)*, *le [Centre de technologie vidéo d’Adobe](https://www.adobe.com/devnet/video/) et le Open Source Media Framework.
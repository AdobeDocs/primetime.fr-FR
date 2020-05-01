---
description: Pour configurer Adobe® Access™ en vue de son utilisation, copiez les fichiers du DVD. Ces fichiers comprennent des fichiers JAR contenant du code, des certificats et des classes tierces. En outre, demandez un certificat à Adobe Systems Incorporated. Vous recevrez plusieurs informations d’identification utilisées pour protéger l’intégrité du contenu assemblé, des licences et de la communication entre le client et le serveur.
seo-description: Pour configurer Adobe® Access™ en vue de son utilisation, copiez les fichiers du DVD. Ces fichiers comprennent des fichiers JAR contenant du code, des certificats et des classes tierces. En outre, demandez un certificat à Adobe Systems Incorporated. Vous recevrez plusieurs informations d’identification utilisées pour protéger l’intégrité du contenu assemblé, des licences et de la communication entre le client et le serveur.
seo-title: Configuration de l'environnement de développement
title: Configuration de l'environnement de développement
uuid: 1f192783-9c9a-4342-909a-4881248a85ad
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Configuration du SDK {#setting-up-the-sdk}

Pour configurer Adobe® Access™ en vue de son utilisation, copiez les fichiers du DVD. Ces fichiers comprennent des fichiers JAR contenant du code, des certificats et des classes tierces. En outre, demandez un certificat à Adobe Systems Incorporated. Vous recevrez plusieurs informations d’identification utilisées pour protéger l’intégrité du contenu assemblé, des licences et de la communication entre le client et le serveur.

Le SDK Adobe Access est disponible en deux types :
* Adobe Access Core SDK
* SDK Adobe Access Professional

Le tableau suivant présente une comparaison de base des SDK Adobe Access :

| Fonction | Adobe Access Core SDK | SDK Adobe Access Professional |
|---|---|---|
| Fonctionnalités de Flash Access 2.0 | Disponible | Disponible |
| Rotation clé | - | Disponible |
| Prise en charge des domaines | Disponible | Disponible |
| Chaîne de licence améliorée | Disponible | Disponible |
| Messages de synchronisation | Disponible | Disponible |
| Prégénération de licence | Disponible | Disponible |
| Licences incorporées | Disponible | Disponible |

## Configuration de l&#39;environnement de développement {#setting-up-the-development-environment}

A partir du DVD, copiez les fichiers SDK suivants pour les utiliser dans votre environnement de développement et votre chemin de classe Java :

* adobe-flashaccess-certs.jar (contient les certificats racine Adobe)
* adobe-flashaccess-sdk.jar (contient les classes du SDK principal Adobe Access)
* adobe-flashaccess-sdk-pro.jar (contient les classes du SDK Adobe Access Professional, requises uniquement pour les fonctionnalités professionnelles)

Vous avez besoin des fichiers JAR tiers suivants situés également sur le DVD dans le dossier &quot;third party&quot; du SDK :

* bcmail-jdk15-141.jar
* bcprov-jdk15-141.jar
* commons-découverte-0.4.jar
* commons-logging-1.1.1.jar
* cryptoj.jar
* jaxb-api.jar
* jaxb-impl.jar
* jaxb-libs.jar
* relaxngDatatype.jar
* rm-pdrl.jar
* xsdlib.jar

Pour améliorer les performances, vous pouvez éventuellement activer la prise en charge native des opérations de cryptographie en déployant les bibliothèques spécifiques à la plate-forme situées dans le dossier &quot;thirdparty/cryptoj&quot; du SDK. Pour activer la prise en charge native, ajoutez la bibliothèque de votre plate-forme (jsafe.dll pour Windows ou libjsafe.so pour Linux) au chemin d’accès. Les versions 32 bits et 64 bits de ces bibliothèques sont fournies. (Notez que la version 64 bits ne doit être utilisée que si vous disposez d’un système d’exploitation 64 bits et que vous exécutez la version 64 bits de Java).

En outre, une partie facultative du SDK est adobe-flashaccess-lcrm.jar. Ce fichier n’est nécessaire que pour les fonctionnalités liées à la compatibilité d’Adobe Flash Media Rights Management Server (FMRMS) 1.x. Si vous avez déjà déployé FMRMS 1.x et ne souhaitez pas recréer le package de votre contenu protégé par FMRMS, vous devez ajouter la prise en charge à votre serveur de licences afin qu’il puisse gérer les anciens contenus et clients.

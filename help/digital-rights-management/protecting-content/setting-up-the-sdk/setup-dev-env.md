---
description: Si vous souhaitez configurer Primetime DRM, copiez les fichiers du DVD. Ces fichiers comprennent des fichiers JAR qui incluent du code, des certificats et des classes tierces. En outre, vous devez demander un certificat à Adobe Systems, Incorporated. Adobe vous envoie ensuite plusieurs informations d’identification que vous utilisez pour protéger l’intégrité du contenu, des licences et de la communication contenus dans votre pack entre le client et le serveur.
seo-description: Si vous souhaitez configurer Primetime DRM, copiez les fichiers du DVD. Ces fichiers comprennent des fichiers JAR qui incluent du code, des certificats et des classes tierces. En outre, vous devez demander un certificat à Adobe Systems, Incorporated. Adobe vous envoie ensuite plusieurs informations d’identification que vous utilisez pour protéger l’intégrité du contenu, des licences et de la communication contenus dans votre pack entre le client et le serveur.
seo-title: Configuration de votre environnement de développement
title: Configuration de votre environnement de développement
uuid: 68afefe8-7ec6-466e-89a8-bc0da8afb4c8
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---


# Configuration de votre environnement de développement {#set-up-your-development-environment}

Si vous souhaitez configurer Primetime DRM, copiez les fichiers du DVD. Ces fichiers comprennent des fichiers JAR qui incluent du code, des certificats et des classes tierces. En outre, vous devez demander un certificat à Adobe Systems, Incorporated. Adobe vous envoie ensuite plusieurs informations d’identification que vous utilisez pour protéger l’intégrité du contenu, des licences et de la communication contenus dans votre pack entre le client et le serveur.

Adobe fournit le SDK DRM Primetime sur DVD :

1. Copiez les fichiers suivants de [ !DNL [DVD DRM]/SDK/] dans votre système de développement (sur votre chemin de classe Java) :

   * [!DNL adobe-flashaccess-certs.jar] - Inclut des certificats racine d&#39;Adobe
   * [!DNL adobe-flashaccess-sdk.jar] - Inclut les classes SDK principaux DRM Primetime
   * [!DNL adobe-flashaccess-sdk-pro.jar] - Inclut des classes SDK DRM Professional Primetime, requises uniquement pour les fonctionnalités professionnelles

1. Copiez les fichiers suivants de [ !DNL [DVD DRM]/SDK/thirdparty] vers votre système de développement :

   * [!DNL bcmail-jdk15-141.jar]
   * [!DNL bcprov-jdk15-141.jar]
   * [!DNL commons-discovery-0.4.jar]
   * [!DNL commons-logging-1.1.1.jar]
   * [!DNL cryptoj.jar]
   * [!DNL jaxb-api.jar]
   * [!DNL jaxb-impl.jar]
   * [!DNL jaxb-libs.jar]
   * [!DNL relaxngDatatype.jar]
   * [!DNL rm-pdrl.jar]
   * [!DNL xsdlib.jar]
   * [!DNL jackson-annotations-2.4.0-rc4-20140522.175222-3.jar]
   * [!DNL jackson-core--2.4.0-rc4-20140529.184520-13.jar]
   * [!DNL jackson-databind-2.4.0-rc4-20140603.005043-38.jar]

1. (Facultatif) Pour améliorer les performances, vous pouvez activer la prise en charge native des opérations de cryptographie en copiant la bibliothèque spécifique à la plate-forme appropriée de [ !DNL [DVD DRM]/SDK/thirdparty/cryptoj/] dans votre système de développement (pensez à placer l’emplacement sur votre chemin) :

   * [!DNL jsafe.dll] - Windows
   * [!DNL libjsafe.so] - Linux

      >[!NOTE]
      >
      >Les versions 32 bits et 64 bits de ces bibliothèques sont disponibles. Vous ne devez utiliser la version 64 bits que si vous disposez d’un système d’exploitation 64 bits et que vous exécutez la version 64 bits de Java.

1. (Facultatif) Pour les fonctionnalités liées à la compatibilité FMRMS (Adobe Flash Media Rights Management Server) 1.x, copiez `[DRM DVD]/SDK/adobe-flashaccess-lcrm.jar]` dans votre système de développement :

   Déployez cette application uniquement si vous avez déjà déployé FMRMS 1.x et ne souhaitez pas regrouper à nouveau votre contenu protégé par FMRMS. Dans ce cas, vous devez ajouter cette prise en charge à votre serveur de licences afin qu’il puisse gérer les anciens contenus et clients.

---
title: Déploiement du serveur DRM Adobe Primetime pour la diffusion en continu protégée
description: Déploiement du serveur DRM Adobe Primetime pour la diffusion en continu protégée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Déploiement du serveur DRM Adobe Primetime pour la diffusion en continu protégée{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Avant de pouvoir déployer Adobe Primetime DRM Server for Protected Streaming, vous devez avoir installé les versions de Java et Tomcat répertoriées dans la rubrique Exigences .

Le package Primetime DRM Server for Protected Streaming inclut [!DNL flashaccesserver.war]. Si vous :

* Pour déployer ce fichier WAR, vous devez le copier dans le fichier Tomcat. [!DNL webapps] répertoire .
* Ayant déjà déployé le fichier WAR, vous devrez peut-être supprimer le répertoire WAR décompressé ( [!DNL flashaccessserver] chez Tomcat [!DNL webapps] ).

* Pour empêcher Tomcat de décompresser les fichiers WAR, modifiez la variable [!DNL server.xml] dans le fichier Tomcat [!DNL conf] et configurez la variable `unpackWARs` en la définissant sur `false`.

>[!NOTE]
>
>Si vous avez configuré Tomcat pour inclure [!DNL commons-logging.jar] sur le chemin d’accès aux classes du système (non requis pour le serveur DRM Primetime pour la diffusion en continu protégée), vous devez configurer la journalisation des ressources communes pour utiliser Log4J.

Le serveur utilise éventuellement une bibliothèque spécifique à la plateforme ( [!DNL jsafe.dll] sous Microsoft Windows ou [!DNL libjsafe.so] sous Linux pour des performances optimales. Vous pouvez copier la bibliothèque appropriée pour votre plateforme depuis [!DNL thirdparty/cryptoj/]*platform* à un emplacement spécifié par la variable `PATH` variable d’environnement ou `LD_LIBRARY_PATH` sous Linux.

>[!NOTE]
>
>Vous ne devez utiliser la version 64 bits que si le système d’exploitation et le JDK prennent en charge 64 bits. Sinon, vous devez utiliser la version 32 bits.

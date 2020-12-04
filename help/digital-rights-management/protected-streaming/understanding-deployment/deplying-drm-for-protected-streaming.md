---
seo-title: Déploiement du serveur DRM Adobe Primetime pour la diffusion en continu protégée
title: Déploiement du serveur DRM Adobe Primetime pour la diffusion en continu protégée
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Déploiement du serveur DRM Adobe Primetime pour la diffusion en flux continu protégée {#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Avant de pouvoir déployer Adobe Primetime DRM Server for Protected Streaming, vous devez avoir installé les versions de Java et Tomcat répertoriées dans la rubrique Conditions requises.

Le package Primetime DRM Server for Protected Streaming inclut [!DNL flashaccesserver.war]. Si :

* Pour déployer ce fichier WAR, vous devez le copier dans le répertoire [!DNL webapps] de Tomcat.
* Ayant déjà déployé le fichier WAR, vous devrez peut-être supprimer le répertoire WAR décompressé ( [!DNL flashaccessserver] dans le répertoire [!DNL webapps] de Tomcat).

* Pour empêcher Tomcat de décompresser les fichiers WAR, modifiez le fichier [!DNL server.xml] dans le répertoire [!DNL conf] de Tomcat et configurez l&#39;attribut `unpackWARs` en le définissant sur `false`.

>[!NOTE]
>
>Si vous avez configuré Tomcat pour inclure [!DNL commons-logging.jar] dans le chemin de classe du système (non requis pour le serveur DRM Primetime pour la diffusion en flux continu protégée), vous devez configurer la journalisation des biens communs pour utiliser Log4J.

Le serveur utilise éventuellement une bibliothèque spécifique à la plate-forme ( [!DNL jsafe.dll] sous Microsoft Windows ou [!DNL libjsafe.so] sous Linux pour des performances optimales. Vous pouvez copier la bibliothèque appropriée pour votre plateforme de [!DNL thirdparty/cryptoj/]*plateforme* vers un emplacement spécifié par la variable d&#39;environnement `PATH` ou `LD_LIBRARY_PATH` sous Linux.

>[!NOTE]
>
>Vous ne devez utiliser la version 64 bits que si le système d’exploitation et le JDK prennent en charge la version 64 bits. Sinon, vous devez utiliser la version 32 bits.


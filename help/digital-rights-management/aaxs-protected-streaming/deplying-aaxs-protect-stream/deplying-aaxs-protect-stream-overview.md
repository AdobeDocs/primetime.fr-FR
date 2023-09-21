---
title: Présentation du déploiement d’Adobe Access Server for Protected Streaming
description: Présentation du déploiement d’Adobe Access Server for Protected Streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Présentation du déploiement d’Adobe Access Server for Protected Streaming {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Avant de déployer Adobe Access Server for Protected Streaming, assurez-vous d’avoir installé les versions de Java et Tomcat répertoriées dans la section Exigences .

Le package Adobe Access Server for Protected Streaming inclut [!DNL flashaccesserver.war]. Pour déployer ce fichier WAR, copiez-le dans le fichier Tomcat [!DNL webapps] répertoire . Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement le répertoire WAR décompressé ( [!DNL flashaccessserver] chez Tomcat [!DNL webapps] ). Pour empêcher Tomcat de décompresser des fichiers WAR, modifiez la variable [!DNL server.xml] dans le fichier Tomcat [!DNL conf] et définissez `unpackWARs` Attribuer à `false`.

>[!NOTE]
>
>Si vous avez configuré Tomcat pour inclure [!DNL commons-logging.jar] sur le chemin d’accès aux classes système (non requis pour la diffusion en continu protégée d’Adobe Access Server), la journalisation des ressources communes doit être configurée pour utiliser Log4J.

Le serveur utilise éventuellement une bibliothèque spécifique à la plateforme ( [!DNL jsafe.dll] sous Microsoft Windows ou [!DNL libjsafe.so] sous Linux) pour des performances optimales. Copiez la bibliothèque appropriée pour votre plateforme depuis [!DNL thirdparty/cryptoj/]*platform* à un emplacement spécifié par la variable `PATH` variable d’environnement (ou `LD_LIBRARY_PATH` sous Linux).

>[!NOTE]
>
>La version 64 bits ne doit être utilisée que si le système d’exploitation et le JDK prennent en charge la version 64 bits, sinon utilisez la version 32 bits.

---
seo-title: Présentation du déploiement d’Adobe Access Server pour la diffusion en flux continu protégée
title: Présentation du déploiement d’Adobe Access Server pour la diffusion en flux continu protégée
uuid: 48a7e452-520a-4ff8-97e9-11210221256d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# Présentation du déploiement d’Adobe Access Server pour la diffusion en flux continu protégée {#deploying-the-adobe-access-server-for-protected-streaming-overview}

Avant de déployer Adobe Access Server for Protected Streaming, assurez-vous d’avoir installé les versions de Java et Tomcat répertoriées dans la section Conditions requises.

Le package Adobe Access Server for Protected Streaming inclut [!DNL flashaccesserver.war]. Pour déployer ce fichier WAR, copiez-le dans le [!DNL webapps] répertoire de Tomcat. Si vous avez déjà déployé le fichier WAR, vous devrez peut-être supprimer manuellement le répertoire WAR décompressé ( [!DNL flashaccessserver] dans le [!DNL webapps] répertoire de Tomcat). Pour empêcher Tomcat de décompresser les fichiers WAR, modifiez le [!DNL server.xml] fichier dans le [!DNL conf] répertoire de Tomcat et définissez l’ `unpackWARs` attribut sur `false`.

>[!NOTE]
>
>Si vous avez configuré Tomcat pour inclure [!DNL commons-logging.jar] le chemin de classe System (non requis pour la diffusion en flux continu protégée Adobe Access Server), la journalisation des ressources communes doit être configurée pour utiliser Log4J.

Le serveur utilise éventuellement une bibliothèque spécifique à la plate-forme ( [!DNL jsafe.dll] sous Microsoft Windows ou [!DNL libjsafe.so] sous Linux) pour des performances optimales. Copiez la bibliothèque appropriée pour votre plateforme de la [!DNL thirdparty/cryptoj/]*plateforme *vers un emplacement spécifié par la variable d’`PATH`environnement (ou`LD_LIBRARY_PATH`sous Linux).

>[!NOTE]
>
>La version 64 bits ne doit être utilisée que si le système d’exploitation et le JDK prennent en charge la version 64 bits, sinon la version 32 bits.


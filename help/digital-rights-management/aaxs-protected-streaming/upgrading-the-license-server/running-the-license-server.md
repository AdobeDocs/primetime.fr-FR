---
description: Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccserver.war déployé sur votre serveur d’applications par le fichier inclus avec le dernier Adobe Access. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-locataire.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec le dernier Adobe Access.
seo-description: Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccserver.war déployé sur votre serveur d’applications par le fichier inclus avec le dernier Adobe Access. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-locataire.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec le dernier Adobe Access.
seo-title: Exécution de Adobe Access Server pour la diffusion en continu protégée
title: Exécution de Adobe Access Server pour la diffusion en continu protégée
uuid: 3819500d-ad2f-49eb-8aa4-e50a55461608
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Exécution de l’Adobe Access Server pour la diffusion en flux continu protégée {#running-the-adobe-access-server-for-protected-streaming}

Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccserver.war déployé sur votre serveur d’applications par le fichier inclus avec le dernier Adobe Access. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-locataire.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec le dernier Adobe Access.

Avant d’exécuter Adobe Access Server for Protected Streaming, l’Adobe vous recommande de vérifier que les fichiers de configuration sont valides en utilisant les utilitaires fournis avec le serveur de licences. Pour plus d’informations, voir &quot;[Configuration Validator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Pour début à Tomcat et au serveur de licences, exécutez &quot;catalina.bat début&quot; ou &quot;catalina.sh début&quot; depuis le répertoire bin de Tomcat.

Une fois le serveur démarré, vérifiez qu’il est correctement configuré en ouvrant *https:// license-server-host:port/flashaccessoserver/locataire-name/flashaccess/license/v1* dans une fenêtre de navigateur. Si la configuration du client a été correctement chargée, un message de confirmation s’affiche.

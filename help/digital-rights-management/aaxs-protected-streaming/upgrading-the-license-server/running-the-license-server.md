---
description: Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccessoserver.war déployé sur votre serveur d’applications par le fichier fourni avec la dernière version d’Adobe Access. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-tenant.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec la dernière version d’Adobe Access.
seo-description: Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccessoserver.war déployé sur votre serveur d’applications par le fichier fourni avec la dernière version d’Adobe Access. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-tenant.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec la dernière version d’Adobe Access.
seo-title: Exécution d’Adobe Access Server for Protected Streaming
title: Exécution d’Adobe Access Server for Protected Streaming
uuid: 3819500d-ad2f-49eb-8aa4-e50a55461608
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Exécution d’Adobe Access Server for Protected Streaming{#running-the-adobe-access-server-for-protected-streaming}

Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccessoserver.war déployé sur votre serveur d’applications par le fichier fourni avec la dernière version d’Adobe Access. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-tenant.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec la dernière version d’Adobe Access.

Avant d’exécuter Adobe Access Server for Protected Streaming, Adobe vous conseille de vérifier que les fichiers de configuration sont valides à l’aide des utilitaires fournis avec le serveur de licences. Pour plus d’informations, voir &quot;[Configuration Validator](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Pour à Tomcat et au serveur de licences, exécutez &quot;catalina.bat&quot; ou &quot;catalina.sh&quot; à partir du répertoire bin de Tomcat.

Une fois le serveur démarré, vérifiez qu’il est correctement configuré en ouvrant *https:// license-server-host:port/flashAccserver/locataire-name/flashaccess/license/v1* dans une fenêtre de navigateur. Si le chargement de la configuration du client a réussi, un message de confirmation s’affiche.

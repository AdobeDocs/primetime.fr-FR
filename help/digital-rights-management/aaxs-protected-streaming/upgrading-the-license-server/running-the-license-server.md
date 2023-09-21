---
description: Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccserver.war déployé sur votre serveur d’applications par le fichier inclus avec le dernier accès Adobe. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-tenant.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec le dernier accès Adobe.
title: Exécution d’Adobe Access Server for Protected Streaming
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Exécution d’Adobe Access Server for Protected Streaming{#running-the-adobe-access-server-for-protected-streaming}

Pour mettre à niveau un serveur exécutant Adobe Access Server for Protected Streaming, remplacez le fichier flashaccserver.war déployé sur votre serveur d’applications par le fichier inclus avec le dernier accès Adobe. Si vous souhaitez utiliser les nouvelles options de configuration décrites ci-dessus, mettez à jour le fichier flashaccess-tenant.xml de votre serveur. Vous devez également mettre à jour jsafe.dll ou libjsafe.so vers la version incluse avec le dernier accès Adobe.

Avant d’exécuter Adobe Access Server for Protected Streaming, Adobe vous recommande de vérifier que les fichiers de configuration sont valides à l’aide des utilitaires fournis avec le serveur de licences. Pour plus d’informations, voir[Validation de configuration](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

Pour démarrer Tomcat et le serveur de licences, exécutez &quot;catalina.bat start&quot; ou &quot;catalina.sh start&quot; à partir du répertoire bin de Tomcat.

Une fois le serveur démarré, vérifiez qu’il est correctement configuré en ouvrant *https:// license-server-host:port/flashaccserver/tenant-name/flashaccess/license/v1* dans une fenêtre de navigateur. Si la configuration du client a été correctement chargée, un message de confirmation s’affiche.

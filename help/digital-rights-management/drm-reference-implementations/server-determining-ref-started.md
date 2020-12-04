---
description: 'null'
seo-description: 'null'
seo-title: Vérifier si le serveur de licences a démarré correctement
title: Vérifier si le serveur de licences a démarré correctement
uuid: a6a034c9-b3c4-4e26-b901-d2c132c00c52
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---


# Vérifiez si le serveur de licences a démarré correctement {#check-whether-the-license-server-started-properly}

Il existe plusieurs méthodes pour déterminer si votre serveur de licence d’implémentation de référence a démarré correctement. Une méthode consiste à vérifier les journaux [!DNL catalina.log], mais cela peut ne pas suffire, car le serveur de licences se connecte à ses propres fichiers journaux.
1. Vérifiez votre fichier [!DNL AdobeFlashAccess.log].

   C’est ici que le serveur de licences d’implémentation de référence écrit les informations de journal. L&#39;emplacement de ce fichier journal est indiqué par votre fichier [!DNL log4j.xml] et peut être modifié pour pointer vers n&#39;importe quel emplacement. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez votre script `catalina` Tomcat.
1. Accédez à l’URL suivante, puis vérifiez que le texte &quot;License Server is setup good&quot; s’affiche :
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]

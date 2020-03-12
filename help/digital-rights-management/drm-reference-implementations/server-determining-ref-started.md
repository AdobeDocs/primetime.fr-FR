---
description: 'null'
seo-description: 'null'
seo-title: Vérifier si le serveur de licences a démarré correctement
title: Vérifier si le serveur de licences a démarré correctement
uuid: a6a034c9-b3c4-4e26-b901-d2c132c00c52
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Vérifier si le serveur de licences a démarré correctement {#check-whether-the-license-server-started-properly}

Il existe plusieurs façons de déterminer si votre serveur de licence d’implémentation de référence a démarré correctement. Une méthode consiste à vérifier les [!DNL catalina.log] journaux, mais cela peut ne pas suffire, car le serveur de licences se connecte à ses propres fichiers journaux.
1. Vérifiez votre [!DNL AdobeFlashAccess.log] fichier.

   C’est là que le serveur de licences d’implémentation de référence écrit les informations du journal. L’emplacement de ce fichier journal est indiqué par votre [!DNL log4j.xml] fichier et peut être modifié pour pointer vers n’importe quel emplacement. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez votre script `catalina` Tomcat.
1. Accédez à l’URL suivante et vérifiez que le texte &quot;License Server is setup correct&quot; s’affiche :
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]

---
title: Vérifiez si le serveur de licences a démarré correctement
description: Vérifiez si le serveur de licences a démarré correctement
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Vérifiez si le serveur de licences a démarré correctement {#check-whether-the-license-server-started-properly}

Il existe plusieurs façons de déterminer si votre serveur de licence de mise en oeuvre de référence a démarré correctement. Une méthode consiste à vérifier la variable [!DNL catalina.log] journaux, mais cela peut ne pas suffire, car le serveur de licences se connecte à ses propres fichiers journaux.
1. Vérifiez vos [!DNL AdobeFlashAccess.log] fichier .

   C’est là que le serveur de licence de mise en oeuvre de référence écrit des informations de journal. L’emplacement de ce fichier journal est indiqué par votre [!DNL log4j.xml] et peuvent être modifiés pour pointer vers n’importe quel emplacement. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez votre `catalina` Script Tomcat.
1. Accédez à l’URL suivante et vérifiez que le texte &quot;License Server is setup good&quot; (Le serveur de licences est configuré correctement) s’affiche :
   [!DNL ht<span></span>tps://localhost:8080/flashaccess/license/v4]

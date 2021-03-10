---
title: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
description: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Détermination de l&#39;exécution correcte du serveur de licences d&#39;implémentation des références {#determining-if-reference-implementation-license-server-is-running-properly}

Il existe plusieurs méthodes pour déterminer si votre serveur a démarré correctement. L’affichage des journaux [!DNL catalina.log] peut ne pas suffire, car le serveur de licences se connecte à ses propres fichiers journaux. Suivez les étapes ci-dessous pour vous assurer que votre implémentation de référence a démarré correctement.

* Vérifiez votre fichier [!DNL AdobeFlashAccess.log]. C’est ici que l’implémentation de référence écrit les informations du journal. L&#39;emplacement de ce fichier journal est indiqué par votre fichier [!DNL log4j.xml] et peut être modifié pour pointer vers l&#39;emplacement de votre choix. Par défaut, le fichier journal est généré dans le répertoire de travail dans lequel vous avez exécuté catalina.

* Accédez à l’URL suivante : `https:///flashaccess/license/v4<your server:server port>`. Le texte &quot;License Server is setup correct&quot; doit s’afficher.

Une autre façon de tester si votre serveur s’exécute correctement consiste à assembler un élément de contenu de test, à configurer un exemple de lecteur vidéo et à le lire. La procédure suivante décrit ce processus :

1. Accédez au dossier [!DNL \Reference Implementation\Command Line Tools]. Pour plus d&#39;informations sur l&#39;installation des outils de ligne de commande, voir [Installation des outils de ligne de commande](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools).

1. Créez une stratégie anonyme simple à l’aide de la commande suivante :

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Pour plus d&#39;informations sur la création de stratégies à l&#39;aide de Policy Manager, consultez [Utilisation de la ligne de commande](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. Définissez la propriété `encrypt.license.serverurl` du fichier [!DNL flashaccesstools.properties] sur l’URL du serveur de licences (par exemple, `https:// localhost:8080/`). Le fichier [!DNL flashaccesstools.properties] se trouve sous le dossier [!DNL \Reference Implementation\Command Line Tools].

1. Empaquetez un élément de contenu à l’aide de la commande suivante :

   ```java
       java -jar libs\AdobePackager.jar  
   <i class="+ topic ph hi-d="" i "="">
   test_input_FLV  
   <i class="+ topic ph hi-d="" i "="">
   output_file  
               -p policy_test.pol 
   </i class="+ topic> 
   </i class="+ topic>
   ```

1. Copiez les 2 fichiers générés dans le dossier Tomcat [!DNL webapps\ROOT\Content].
1. Accédez à `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` et copiez le contenu dans le dossier Tomcat `webapps\ROOT\SVP\`.
1. Installez Flash Player 10.1 ou version ultérieure.
1. Ouvrez le navigateur Web et accédez à l’URL suivante :

   `https:// localhost:8080/SVP/player.html`
1. Accédez à l’URL suivante, puis cliquez sur le bouton Lecture :

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Si la lecture de la vidéo échoue, vérifiez si des codes d’erreur ont été écrits dans le volet de journalisation de l’exemple de lecteur vidéo ou dans le fichier `AdobeFlashAccess.log`. L’emplacement du fichier journal `AdobeFlashAccess.log` est indiqué par votre fichier log4j.xml et peut être modifié pour pointer vers l’emplacement de votre choix. Par défaut, le fichier journal est écrit dans le répertoire de travail dans lequel vous avez exécuté catalina.

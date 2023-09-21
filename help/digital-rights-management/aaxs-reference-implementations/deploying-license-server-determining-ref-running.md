---
title: Déterminer si le serveur de licence d’implémentation de référence s’exécute correctement
description: Déterminer si le serveur de licence d’implémentation de référence s’exécute correctement
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Déterminer si le serveur de licence d’implémentation de référence s’exécute correctement {#determining-if-reference-implementation-license-server-is-running-properly}

Il existe plusieurs façons de déterminer si votre serveur a démarré correctement. Affichage de la [!DNL catalina.log] Les journaux peuvent ne pas être suffisants, car le serveur de licences se connecte à ses propres fichiers journaux. Suivez les étapes ci-dessous pour vous assurer que votre implémentation de référence a démarré correctement.

* Vérifiez vos [!DNL AdobeFlashAccess.log] fichier . C’est là que l’implémentation de référence écrit des informations de journal. L’emplacement de ce fichier journal est indiqué par votre [!DNL log4j.xml] et peuvent être modifiés pour pointer vers n’importe quel emplacement de votre choix. Par défaut, le fichier journal est généré dans le répertoire de travail dans lequel vous avez exécuté catalina.

* Accédez à l’URL suivante : `https:///flashaccess/license/v4<your server:server port>`. Le texte &quot;Le serveur de licences est configuré correctement&quot; devrait s’afficher.

Une autre manière de tester si votre serveur s’exécute correctement consiste à regrouper un contenu de test, à configurer un exemple de lecteur vidéo et à le lire. La procédure suivante décrit ce processus :

1. Accédez au [!DNL \Reference Implementation\Command Line Tools] dossier. Pour plus d’informations sur l’installation des outils de ligne de commande, voir [Installation des outils de ligne de commande](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools).

1. Créez une stratégie anonyme simple à l’aide de la commande suivante :

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Pour plus d’informations sur la création de stratégies à l’aide du Gestionnaire de stratégies, voir [Utilisation de la ligne de commande](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. Définissez la variable `encrypt.license.serverurl` dans la propriété [!DNL flashaccesstools.properties] à l’URL du serveur de licences (par exemple, `https:// localhost:8080/`). La variable [!DNL flashaccesstools.properties] se trouve sous le fichier [!DNL \Reference Implementation\Command Line Tools] dossier.

1. Regroupez un élément de contenu à l’aide de la commande suivante :

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

1. Copiez les 2 fichiers générés dans le Tomcat [!DNL webapps\ROOT\Content] dossier.
1. Accédez à `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` et copier le contenu dans le Tomcat `webapps\ROOT\SVP\` dossier.
1. Installez Flash Player 10.1 ou version ultérieure.
1. Ouvrez le navigateur web et accédez à l’URL suivante :

   `https:// localhost:8080/SVP/player.html`
1. Accédez à l’URL suivante, puis cliquez sur le bouton Lecture :

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Si la lecture de la vidéo échoue, vérifiez si des codes d’erreur ont été écrits dans le volet de journalisation de l’exemple de lecteur vidéo ou dans le `AdobeFlashAccess.log` fichier . L’emplacement du `AdobeFlashAccess.log` Le fichier journal est indiqué par votre fichier log4j.xml et peut être modifié pour pointer vers n’importe quel emplacement. Par défaut, le fichier journal est écrit dans le répertoire de travail dans lequel vous avez exécuté catalina.

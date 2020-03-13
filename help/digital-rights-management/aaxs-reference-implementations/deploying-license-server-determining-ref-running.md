---
description: 'null'
seo-description: 'null'
seo-title: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
title: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
uuid: 84d32c94-7594-464e-a883-5338b52de2bf
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Détermination de l’exécution correcte du serveur de licences d’implémentation des références {#determining-if-reference-implementation-license-server-is-running-properly}

Il existe plusieurs façons de déterminer si votre serveur a démarré correctement. L’affichage des [!DNL catalina.log] journaux peut ne pas suffire, car le serveur de licences se connecte à ses propres fichiers journaux. Suivez les étapes ci-dessous pour vous assurer que votre implémentation des références a démarré correctement.

* Vérifiez votre [!DNL AdobeFlashAccess.log] fichier. C’est là que l’implémentation de référence écrit les informations du journal. L&#39;emplacement de ce fichier journal est indiqué par votre [!DNL log4j.xml] fichier et peut être modifié pour pointer vers n&#39;importe quel emplacement de votre choix. Par défaut, le fichier journal est généré dans le répertoire de travail dans lequel vous avez exécuté catalina.

* Accédez à l’URL suivante : `https:///flashaccess/license/v4<your server:server port>`. Le texte &quot;Le serveur de licences est configuré correctement&quot; doit s’afficher.

Une autre manière de tester si votre serveur s’exécute correctement consiste à assembler un élément de contenu de test, à configurer un exemple de lecteur vidéo et à le lire. La procédure suivante décrit ce processus :

1. Accédez au [!DNL \Reference Implementation\Command Line Tools] dossier. Pour plus d’informations sur l’installation des outils de ligne de commande, voir [Installation des outils](../aaxs-reference-implementations/command-line-tools/aaxs-ref-impl-command-line-overview.md#installing-the-command-line-tools)de ligne de commande.

1. Créez une stratégie anonyme simple à l’aide de la commande suivante :

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Pour plus d’informations sur la création de stratégies à l’aide du Gestionnaire de stratégies, voir Utilisation des lignes de [commande](../aaxs-reference-implementations/command-line-tools/policy-manager/command-line-usage.md).

1. Définissez la `encrypt.license.serverurl` propriété du [!DNL flashaccesstools.properties] fichier sur l’URL du serveur de licences (par exemple `https:// localhost:8080/`). Le [!DNL flashaccesstools.properties] fichier se trouve sous le [!DNL \Reference Implementation\Command Line Tools] dossier.

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

1. Copiez les 2 fichiers générés dans le dossier Tomcat [!DNL webapps\ROOT\Content] .
1. Accédez au dossier Tomcat `Reference Implementation\Sample Video Players\Desktop\Flash Player\Release` et copiez-le dans ce dossier `webapps\ROOT\SVP\` .
1. Installez Flash Player 10.1 ou version ultérieure.
1. Ouvrez le navigateur Web et accédez à l’URL suivante :

   `https:// localhost:8080/SVP/player.html`
1. Accédez à l’URL suivante, puis cliquez sur le bouton Lecture :

   `https:// localhost:8080/Content/<your_encrypted_FLV>`
1. Si la lecture de la vidéo échoue, vérifiez si des codes d’erreur ont été écrits dans le volet de journalisation de l’exemple de lecteur vidéo ou dans le `AdobeFlashAccess.log` fichier. L’emplacement du fichier `AdobeFlashAccess.log` journal est indiqué par votre fichier log4j.xml et peut être modifié pour pointer vers n’importe quel emplacement de votre choix. Par défaut, le fichier journal est écrit dans le répertoire de travail dans lequel vous avez exécuté catalina.

---
description: 'null'
seo-description: 'null'
seo-title: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
title: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
uuid: afd82d6d-a11c-48ff-b48c-8f81d4b406a0
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# Détermination de l’exécution correcte du serveur de licences d’implémentation des références {#determining-if-reference-implementation-license-server-runs-properly}

Il existe plusieurs méthodes pour déterminer si votre serveur de licence d’implémentation de référence a démarré correctement. Vous pouvez vue que les [!DNL catalina.log] journaux ne sont pas suffisants, car le serveur de licences se connecte à ses propres fichiers journaux. Suivez les étapes ci-dessous pour vous assurer que votre implémentation de référence a démarré correctement.

* Vérifiez votre [!DNL AdobeFlashAccess.log] fichier. C’est ici que l’implémentation de référence écrit les informations du journal. L&#39;emplacement de ce fichier journal est indiqué par votre [!DNL log4j.xml] fichier et peut être modifié pour pointer vers l&#39;emplacement de votre choix. Par défaut, le fichier journal copié dans le répertoire de travail dans lequel vous exécutez catalina.

* Accédez à l’URL suivante : [!DNL https:// flashaccess/license/v4]*port *server:server. Le texte &quot;License Server is setup correct&quot; doit s’afficher.

Une autre façon de tester si votre serveur s’exécute correctement consiste à assembler un segment du contenu du test, à configurer un exemple de lecteur vidéo, puis à le lire.

La procédure suivante décrit ce processus :

1. Accédez au [!DNL \Reference Implementation\Command Line Tools] dossier.

   Voir [Installation des outils](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) de ligne de commande pour savoir comment installer les outils de ligne de commande.

1. Saisissez la commande suivante pour créer une stratégie DRM anonyme simple :

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Voir Utilisation [de la ligne de](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) commande pour savoir comment créer des stratégies DRM à l&#39;aide du Gestionnaire de stratégies DRM.

1. Définissez la `encrypt.license.serverurl` propriété du [!DNL flashaccesstools.properties] fichier sur l’URL du serveur de licences.

   Par exemple, [!DNL https:// localhost:8080/]. Le [!DNL flashaccesstools.properties] fichier se trouve dans le [!DNL \Reference Implementation\Command Line Tools] dossier.

1. Saisissez la commande suivante pour compresser un segment du contenu :

```
       java -jar libs\AdobePackager.jar  
       <i class="+ topic ph hi-d="" i "="">
         test_input_FLV  
        <i class="+ topic ph hi-d="" i "="">
       output_file  
               -p policy_test.pol 
       </i class="+ topic> 
       </i class="+ topic>
```

1. Copiez les deux fichiers générés dans le [!DNL webapps\ROOT\Content] dossier du serveur Tomcat.
1. Accédez au [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] répertoire et copiez le contenu dans le dossier [ !DNL webapps\ROOT\SVP\] sur le serveur Tomcat.

1. Installez Flash Player version 10.1 ou ultérieure.
1. Ouvrez un navigateur Web et accédez à l’URL suivante : [!DNL        https:// localhost:8080/SVP/player.html]

1. Accédez à l’URL suivante, puis cliquez sur **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. Si la lecture de la vidéo échoue, vérifiez si des codes d’erreur s’affichent dans le volet de journalisation de l’exemple de lecteur vidéo ou s’ils sont ajoutés au [!DNL AdobeFlashAccess.log] fichier.

   Vous pouvez maintenant rechercher l’emplacement du fichier [!DNL AdobeFlashAccess.log] journal dans le fichier log4j.xml, puis le modifier. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez catalina.


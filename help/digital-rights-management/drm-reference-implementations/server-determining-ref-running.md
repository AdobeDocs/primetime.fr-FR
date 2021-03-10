---
title: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
description: Détermination de l’exécution correcte du serveur de licences d’implémentation des références
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# Détermination de l&#39;exécution correcte du serveur de licences d&#39;implémentation de référence {#determining-if-reference-implementation-license-server-runs-properly}

Il existe plusieurs méthodes pour déterminer si votre serveur de licence d’implémentation de référence a démarré correctement. Vous pouvez vue les journaux [!DNL catalina.log] peut ne pas suffire, car le serveur de licences se connecte à ses propres fichiers journaux. Suivez les étapes ci-dessous pour vous assurer que votre implémentation de référence a démarré correctement.

* Vérifiez votre fichier [!DNL AdobeFlashAccess.log]. C’est ici que l’implémentation de référence écrit les informations du journal. L&#39;emplacement de ce fichier journal est indiqué par votre fichier [!DNL log4j.xml] et peut être modifié pour pointer vers l&#39;emplacement de votre choix. Par défaut, le fichier journal copié dans le répertoire de travail dans lequel vous exécutez catalina.

* Accédez à l’URL suivante : [!DNL https:// flashaccess/license/v4]*port serveur:port serveur*. Le texte &quot;License Server is setup correct&quot; doit s’afficher.

Une autre façon de tester si votre serveur s’exécute correctement consiste à assembler un segment du contenu du test, à configurer un exemple de lecteur vidéo, puis à le lire.

La procédure suivante décrit ce processus :

1. Accédez au dossier [!DNL \Reference Implementation\Command Line Tools].

   Voir [Installation des outils de ligne de commande](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) pour savoir comment installer les outils de ligne de commande.

1. Saisissez la commande suivante pour créer une stratégie DRM anonyme simple :

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Voir [Utilisation de la ligne de commande](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) pour savoir comment créer des stratégies DRM avec le Gestionnaire de stratégies DRM.

1. Définissez la propriété `encrypt.license.serverurl` du fichier [!DNL flashaccesstools.properties] sur l’URL du serveur de licences.

   Par exemple, [!DNL https:// localhost:8080/]. Le fichier [!DNL flashaccesstools.properties] se trouve dans le dossier [!DNL \Reference Implementation\Command Line Tools].

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

1. Copiez les deux fichiers générés dans le dossier [!DNL webapps\ROOT\Content] du serveur Tomcat.
1. Accédez au répertoire [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] et copiez le contenu dans le dossier [!DNL webapps\ROOT\SVP\] du serveur Tomcat.

1. Installez Flash Player version 10.1 ou ultérieure.
1. Ouvrez un navigateur Web et accédez à l’URL suivante : [!DNL        https:// localhost:8080/SVP/player.html]

1. Accédez à l’URL suivante, puis cliquez sur **[!UICONTROL Play]** : [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. Si la lecture de la vidéo échoue, vérifiez si des codes d’erreur s’affichent dans le volet de journalisation de l’exemple de lecteur vidéo ou s’ils sont ajoutés au fichier [!DNL AdobeFlashAccess.log].

   Vous pouvez maintenant rechercher l’emplacement du fichier journal [!DNL AdobeFlashAccess.log] dans le fichier log4j.xml, puis le modifier. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez catalina.


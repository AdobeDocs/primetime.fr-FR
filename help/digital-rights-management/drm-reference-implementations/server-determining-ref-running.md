---
title: Déterminer si le serveur de licence d’implémentation de référence s’exécute correctement
description: Déterminer si le serveur de licence d’implémentation de référence s’exécute correctement
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Déterminer si le serveur de licence d’implémentation de référence s’exécute correctement {#determining-if-reference-implementation-license-server-runs-properly}

Il existe plusieurs façons de déterminer si votre serveur de licence de mise en oeuvre de référence a démarré correctement. Vous pouvez afficher la [!DNL catalina.log] Les journaux peuvent ne pas être suffisants, car le serveur de licences se connecte à ses propres fichiers journaux. Suivez les étapes ci-dessous pour vous assurer que votre implémentation de référence a démarré correctement.

* Vérifiez vos [!DNL AdobeFlashAccess.log] fichier . C’est là que l’implémentation de référence écrit des informations de journal. L’emplacement de ce fichier journal est indiqué par votre [!DNL log4j.xml] et peuvent être modifiés pour pointer vers n’importe quel emplacement de votre choix. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez catalina.

* Accédez à l’URL suivante : [!DNL https:// flashaccess/license/v4]*votre serveur : port du serveur*. Le texte &quot;Le serveur de licences est configuré correctement&quot; devrait s’afficher.

Une autre manière de tester si votre serveur s’exécute correctement consiste à regrouper un segment du contenu du test, à configurer un exemple de lecteur vidéo, puis à le lire.

La procédure suivante décrit ce processus :

1. Accédez au [!DNL \Reference Implementation\Command Line Tools] dossier.

   Voir [Installation des outils de ligne de commande](../drm-reference-implementations/command-line-tools/install-command-line-tools.md) sur l’installation des outils de ligne de commande.

1. Saisissez la commande suivante pour créer une stratégie DRM anonyme simple :

   ```
       java -jar libs\AdobePolicyManager.jar new policy_test.pol -x
   ```

   Voir [Utilisation de la ligne de commande](../drm-reference-implementations/command-line-tools/configure-command-line-tools/policy-manager/policy-manager-command-line-usage.md) sur la création de stratégies DRM à l’aide du Gestionnaire de stratégies DRM.

1. Définissez la variable `encrypt.license.serverurl` dans la propriété [!DNL flashaccesstools.properties] à l’URL du serveur de licences.

   Par exemple : [!DNL https:// localhost:8080/]. La variable [!DNL flashaccesstools.properties] se trouve dans le fichier [!DNL \Reference Implementation\Command Line Tools] dossier.

1. Saisissez la commande suivante pour regrouper un segment du contenu :

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

1. Copiez les deux fichiers générés dans le [!DNL webapps\ROOT\Content] sur le serveur Tomcat.
1. Accédez au [!DNL Reference Implementation\Sample Video Players\Desktop\Flash Player\Release] et copiez le contenu dans le répertoire [!DNL webapps\ROOT\SVP\] sur le serveur Tomcat.

1. Installez Flash Player version 10.1 ou ultérieure.
1. Ouvrez un navigateur web et accédez à l’URL suivante : [!DNL        https:// localhost:8080/SVP/player.html]

1. Accédez à l’URL suivante, puis cliquez sur **[!UICONTROL Play]**: [!DNL https:// localhost:8080/Content/] *`your_encrypted_FLV`*.

1. Si la lecture de la vidéo échoue, vérifiez si des codes d’erreur s’affichent dans le volet de journalisation de l’exemple de lecteur vidéo ou s’ils sont ajoutés au [!DNL AdobeFlashAccess.log] fichier .

   Vous pouvez désormais rechercher l’emplacement de la variable [!DNL AdobeFlashAccess.log] fichier journal dans le fichier log4j.xml, puis modifiez-le. Par défaut, le fichier journal est copié dans le répertoire de travail dans lequel vous exécutez catalina.

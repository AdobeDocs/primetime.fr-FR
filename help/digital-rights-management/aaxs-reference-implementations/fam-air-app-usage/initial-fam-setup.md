---
description: 'null'
seo-description: 'null'
seo-title: Configuration initiale de Flash Access Manager
title: Configuration initiale de Flash Access Manager
uuid: e9041f7c-b098-4121-88bf-ff3e6369e01b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Configuration initiale de Flash Access Manager {#initial-flash-access-manager-setup}

Procédez comme suit pour configurer Flash Access Manager :

1. Déployez Packager Server. Ce serveur ne doit être disponible que pour les utilisateurs de votre pare-feu (ne déployez pas ce logiciel sur un ordinateur public). Pour plus d’informations sur le déploiement du serveur, voir [Déploiement du serveur de licences et du gestionnaire de package](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md)de dossiers de contrôle.

   * Copiez [!DNL flashaccess-packager.war] dans le dossier des applications Web de Tomcat.
   * Copiez [!DNL flashaccess-refimpl-packager.properties] des ressources vers un emplacement du chemin de classe.
   *  le serveur. Vous verrez des erreurs dues à des problèmes dans le fichier de propriétés ; cela est attendu car les propriétés n’ont pas encore été remplies.

1. Installez l’application AIR de Flash Access Manager en lançant le [!DNL .air] fichier (nécessite AIR 1.5 ou version ultérieure).
1. Lancez l&#39;application AIR de Flash Access Manager.

   Si votre serveur s’exécute ailleurs [*!DNL https:// localhost:8080*], des erreurs s’affichent indiquant que l’application ne peut pas se connecter au serveur. Fermez la boîte de dialogue d’erreur et renseignez l’URL appropriée pour l’URL du serveur Packager dans l’onglet Préférences. Si le serveur s’exécute à l’URL spécifiée et que le fichier de propriétés se trouve dans le chemin de classe, l’écran Préférences est renseigné avec les valeurs du fichier de propriétés. Après avoir défini l’URL du serveur de packager, l’application AIR mémorise ce paramètre et vous n’aurez pas à le saisir lors du prochain lancement de l’application.
1. Renseignez les valeurs dans l’onglet Préférences et cliquez sur **[!UICONTROL Save]**.
1. Si vous souhaitez utiliser les dossiers de contrôle, vous devez redémarrer le serveur pour récupérer les erreurs que vous avez détectées à l’étape 3. Si les préférences sont configurées correctement, aucune erreur ne doit s’afficher au démarrage.


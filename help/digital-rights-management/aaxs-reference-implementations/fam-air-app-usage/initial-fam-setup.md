---
title: Configuration initiale du Gestionnaire de Flashs Access
description: Configuration initiale du Gestionnaire de Flashs Access
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Configuration initiale du Gestionnaire de Flashs Access {#initial-flash-access-manager-setup}

Pour configurer Flash Access Manager, procédez comme suit :

1. Déployez le serveur Packager. Ce serveur ne doit être disponible que pour les utilisateurs se trouvant dans votre pare-feu (ne déployez pas ce logiciel sur une machine publique). Pour plus d’informations sur le déploiement du serveur, voir [Déploiement du serveur de licences et du gestionnaire de dossiers de contrôle](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md).

   * Copier [!DNL flashaccess-packager.war] au dossier webapps de Tomcat.
   * Copier [!DNL flashaccess-refimpl-packager.properties] des ressources à un emplacement sur le chemin d’accès aux classes.
   * Démarrez le serveur. Des erreurs s’afficheront en raison de problèmes dans le fichier de propriétés ; cela est attendu car les propriétés n’ont pas encore été renseignées.

1. Installez l’application AIR Flash Access Manager en lançant la [!DNL .air] (nécessite AIR 1.5 ou version ultérieure).
1. Lancez l’application AIR Flash Access Manager.

   Si votre serveur s’exécute ailleurs que `https://localhost:8080*`, des erreurs s’affichent indiquant que l’application ne peut pas se connecter au serveur. Fermez la boîte de dialogue d’erreur et renseignez l’URL correcte pour Packager Server URL dans l’onglet Préférences . Si le serveur s’exécute à l’URL spécifiée et que le fichier de propriétés se trouve sur le chemin d’accès aux classes, l’écran Préférences est rempli avec les valeurs du fichier de propriétés. Une fois que vous avez défini l’URL du serveur de package, l’application AIR se souvient de ce paramètre et vous n’aurez pas à le saisir lors du prochain lancement de l’application.
1. Renseignez les valeurs de l’onglet Préférences et cliquez sur **[!UICONTROL Save]**.
1. Si vous souhaitez utiliser les dossiers de contrôle, vous devez redémarrer le serveur pour récupérer les erreurs que vous avez rencontrées à l’étape 3. Si les préférences sont correctement configurées, aucune erreur ne doit s’afficher au démarrage.

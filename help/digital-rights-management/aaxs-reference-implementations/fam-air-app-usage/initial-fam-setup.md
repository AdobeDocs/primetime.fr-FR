---
description: 'null'
seo-description: 'null'
seo-title: Configuration initiale de Flash Access Manager
title: Configuration initiale de Flash Access Manager
uuid: e9041f7c-b098-4121-88bf-ff3e6369e01b
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Configuration initiale de Flash Access Manager {#initial-flash-access-manager-setup}

Pour configurer Flash Access Manager, procédez comme suit :

1. Déployez Packager Server. Ce serveur ne doit être disponible que pour les utilisateurs de votre pare-feu (ne déployez pas ce logiciel sur un ordinateur public). Pour plus d’informations sur le déploiement du serveur, voir [Déploiement du serveur de licences et du gestionnaire de dossiers de contrôle](../../aaxs-reference-implementations/deploying-license-server-and-wfp/deploying-license-server-wfp-overview.md).

   * Copiez [!DNL flashaccess-packager.war] dans le dossier webapps de Tomcat.
   * Copiez [!DNL flashaccess-refimpl-packager.properties] des ressources vers un emplacement du chemin de classe.
   * Début du serveur. Vous verrez des erreurs dues à des problèmes dans le fichier de propriétés ; cela est attendu car les propriétés n&#39;ont pas encore été remplies.

1. Installez l’application AIR de Flash Access Manager en lançant le [!DNL .air] fichier (requiert AIR 1.5 ou version ultérieure).
1. Lancez l’application AIR de Flash Access Manager.

   Si votre serveur s’exécute ailleurs que `https://localhost:8080*`, des erreurs s’affichent indiquant que l’application ne peut pas se connecter au serveur. Fermez la boîte de dialogue d’erreur et renseignez l’URL correcte pour Packager Server URL dans l’onglet Préférences. Si le serveur s’exécute à l’URL spécifiée et que le fichier de propriétés se trouve dans le chemin de classe, l’écran Préférences est renseigné avec les valeurs du fichier de propriétés. Une fois que vous avez défini l’URL du serveur de packager, l’application AIR se souvient de ce paramètre et vous n’aurez pas à le saisir lors du prochain lancement de l’application.
1. Renseignez les valeurs de l’onglet Préférences et cliquez sur **[!UICONTROL Save]**.
1. Si vous souhaitez utiliser les dossiers de contrôle, vous devez redémarrer le serveur pour récupérer les erreurs que vous avez détectées à l’étape 3. Si les préférences sont correctement configurées, aucune erreur ne doit s’afficher au démarrage.


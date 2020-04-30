---
description: Vous pouvez suivre l’utilisation des vidéos dans l’implémentation de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics.
seo-description: Vous pouvez suivre l’utilisation des vidéos dans l’implémentation de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics.
seo-title: Configuration des analyses vidéo
title: Configuration des analyses vidéo
uuid: ce2ebab3-b3c8-472a-9c54-16ddb1c3cc4e
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Configuration des analyses vidéo {#configure-video-analytics}

Vous pouvez suivre l’utilisation des vidéos dans l’implémentation de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics. La mise en oeuvre des références Android est conçue pour envoyer des données d’utilisation de la vidéo et de pulsation à Adobe Analytics. Pour activer cette fonctionnalité, vous devez d’abord contacter votre représentant Adobe Primetime et créer un compte Adobe Analytics.

Vous devez configurer deux emplacements dans l’implémentation des références pour activer l’intégration d’Adobe Analytics. Les configurations d’analyse vidéo à l’exécution prennent effet une fois qu’une nouvelle vidéo est sélectionnée pour la lecture (c.-à-d. une fois qu’une nouvelle PlayerActivity est créée).

1. Configurez les options de temps de chargement dans le fichier `ADBMobileConfig.json` de ressources.

   Ce fichier est fourni par votre représentant Adobe. Il n’est pas inclus par défaut dans le lot du SDK Primetime. Pour plus d&#39;informations sur les paramètres de ce fichier de configuration, consultez le Guide du programmeur Android ici : Initialisez et configurez les analyses vidéo.
1. Configurez les options d’exécution dans le menu Paramètres de mise en oeuvre des références.

   ![](assets/img_psdk_ref_impl_va-settings-menu.png)

   | Options d’exécution | Description |
   |---|---|
   | Serveur de suivi des analyses vidéo | URL du point de terminaison de la collection principale d’analyses vidéo. C’est ici que sont envoyés tous les appels de suivi de pulsation vidéo. |
   | ID de tâche | Identifiant de la tâche de traitement. Ceci indique au point de terminaison principal quel type de traitement appliquer aux appels de suivi vidéo. |
   | Canal | Nom du canal où l’utilisateur regarde le contenu. Pour une application mobile, il s’agit généralement du nom de l’application. |
   | Editeur | Nom de l’éditeur de contenu |
   | Journalisation du débogage | Active la journalisation étendue. Désactivée par défaut, cette option peut avoir un impact sur les performances lorsqu’elle est activée. Vous pouvez donc la désactiver pour un environnement de production. |
   | Mode silencieux | Lorsque cette option est activée, aucun appel réseau n’est effectué. Cela peut donc s’avérer utile pour le débogage local, mais doit être désactivé pour un environnement de production. |
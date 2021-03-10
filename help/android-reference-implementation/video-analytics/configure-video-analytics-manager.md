---
description: Vous pouvez suivre l’utilisation des vidéos dans l’implémentation de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics.
title: Configuration des analyses vidéo
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Configuration des analyses vidéo {#configure-video-analytics}

Vous pouvez suivre l’utilisation des vidéos dans l’implémentation de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics. L’implémentation de référence Android est conçue pour envoyer des données d’utilisation de la vidéo et de pulsation à Adobe Analytics. Pour activer cette fonctionnalité, vous devez d’abord contacter votre représentant Adobe Primetime et créer un compte Adobe Analytics.

Vous devez configurer deux emplacements dans l’implémentation de référence pour activer l’intégration Adobe Analytics. Les configurations d’analyse vidéo à l’exécution prennent effet une fois qu’une nouvelle vidéo est sélectionnée pour la lecture (c.-à-d. une fois qu’une nouvelle PlayerActivity est créée).

1. Configurez les options de temps de chargement dans le fichier de ressources `ADBMobileConfig.json`.

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
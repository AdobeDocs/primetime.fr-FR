---
description: Vous pouvez effectuer le suivi de l’utilisation des vidéos dans la mise en oeuvre de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics.
title: Configuration de Video Analytics
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Configuration de Video Analytics {#configure-video-analytics}

Vous pouvez effectuer le suivi de l’utilisation des vidéos dans la mise en oeuvre de référence Android Primetime en la configurant pour qu’elle fonctionne avec votre compte Adobe Analytics. La mise en oeuvre de référence Android est conçue pour envoyer des données d’utilisation vidéo et de pulsation à Adobe Analytics. Pour activer cette fonctionnalité, vous devez d’abord contacter votre représentant Adobe Primetime et créer un compte Adobe Analytics.

Il existe deux emplacements dans l’implémentation de référence que vous devez configurer pour activer l’intégration Adobe Analytics. Les configurations des analyses vidéo au moment de l’exécution prennent effet lorsqu’une nouvelle vidéo est sélectionnée pour la lecture (c’est-à-dire lorsqu’une nouvelle activité de lecteur est créée).

1. Configurez les options de temps de chargement dans le `ADBMobileConfig.json` fichier de ressources.

   Ce fichier est fourni par votre représentant d’Adobe. Il n’est pas inclus par défaut dans le lot du SDK Primetime. Pour plus d’informations sur les paramètres de ce fichier de configuration, consultez le Guide du programmeur Android dans la rubrique Initialisation et configuration des analyses vidéo.
1. Configuration des options d’exécution dans le menu Paramètres d’implémentation de référence

   ![](assets/img_psdk_ref_impl_va-settings-menu.png)

   | Options d’exécution | Description |
   |---|---|
   | Serveur de suivi Video Analytics | URL du point de terminaison de la collection principale Video Analytics. C’est là que tous les appels de suivi de pulsation vidéo sont envoyés. |
   | ID de tâche | Identifiant de la tâche de traitement. Cela indique au point de terminaison principal quel type de traitement appliquer pour les appels de suivi vidéo. |
   | Canal | Nom du canal sur lequel l’utilisateur visionne le contenu. Il s’agit généralement du nom de l’application mobile. |
   | Éditeur | Nom de l’éditeur de contenu |
   | Journalisation de débogage | Active la journalisation étendue. Désactivé par défaut, cette option peut avoir une incidence sur les performances lorsqu’elle est activée. Cela peut donc être désactivé pour un environnement de production. |
   | Mode silencieux | Lorsque cette option est activée, aucun appel réseau n’est effectué. Cela peut donc s’avérer utile pour le débogage local, mais doit être désactivé pour un environnement de production. |

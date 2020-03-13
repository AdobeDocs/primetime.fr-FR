---
description: Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.
seo-description: Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.
seo-title: Ajouter journalisation et débogage en temps réel
title: Ajouter journalisation et débogage en temps réel
uuid: 568ea2e7-963b-427e-9cb2-e261e4423902
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Ajouter journalisation et débogage en temps réel{#add-real-time-logging-and-debugging}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et la validation sans trop insister sur le système.

>[!IMPORTANT]
>
>La connexion n’est pas incluse dans une configuration de production et ne devrait pas gérer le trafic à fort chargement. Si votre implémentation n’a pas besoin d’être absolument terminée, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications.

1. Créez un thread d’exécution basé sur le minuteur pour votre application vidéo qui  périodiquement les données rassemblées par le système de notification TVSDK.

1. Si l’intervalle du minuteur est trop long et que la taille du  de est trop petite, l’ de la  de notification  débordera. Pour éviter ce débordement, effectuez l’une des opérations suivantes :

   * Réduisez l’intervalle de temps qui déclenche le thread qui interroge les nouveaux .
   * Augmentez la taille du de notification.

1. Sérialisez les entrées de de notification les plus récentes au format JSON et envoyez les entrées à un serveur distant pour le post-traitement.

   Le serveur distant peut alors afficher les données fournies sous forme graphique en temps réel.
1. Pour détecter la perte des  de notification, recherchez les lacunes dans la séquence des valeurs d’index de .

   Chaque  de notification comporte une valeur d’index automatiquement incrémentée par la `NotificationHistory` classe.

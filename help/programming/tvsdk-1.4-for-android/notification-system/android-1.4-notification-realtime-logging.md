---
description: Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.
seo-description: Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.
seo-title: Ajouter journalisation et débogage en temps réel
title: Ajouter journalisation et débogage en temps réel
uuid: 037daf57-a1b3-4b42-ac51-81179fb36915
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Ajouter journalisation et débogage en temps réel{#add-real-time-logging-and-debugging}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et les validations sans trop insister sur le système.

>[!IMPORTANT]
>
>L’extrémité arrière de la journalisation ne fait pas partie d’une configuration de production et ne devrait pas gérer le trafic à forte charge. Si votre implémentation n’a pas besoin d’être complète, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications.

1. Créez un thread d’exécution basé sur un minuteur pour votre application vidéo qui requête périodiquement les données collectées par le système de notification TVSDK.

1. Si l’intervalle du minuteur est trop long et que la taille de la liste du événement est trop petite, la liste du événement de notification déborde. Pour éviter ce débordement, effectuez l’une des opérations suivantes :

   * Réduisez l&#39;intervalle de temps qui conduit le thread qui effectue l&#39;interrogation des nouveaux événements.
   * Augmentez la taille de la liste de notification.

1. Sérialisez les dernières entrées du événement de notification au format JSON et envoyez les entrées à un serveur distant pour post-traitement.

   Le serveur distant peut alors afficher les données fournies sous forme graphique en temps réel.
1. Pour détecter la perte de événements de notification, recherchez des lacunes dans la séquence de valeurs d’index de événement.

   Chaque événement de notification comporte une valeur d’index automatiquement incrémentée par la `session.NotificationHistory` classe.

---
description: Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.
title: Ajouter la journalisation et le débogage en temps réel
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# Ajouter la journalisation et le débogage en temps réel{#add-real-time-logging-and-debugging}

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

   Chaque événement de notification possède une valeur d&#39;index automatiquement incrémentée par la classe `session.NotificationHistory`.

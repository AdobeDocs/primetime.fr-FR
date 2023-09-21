---
description: Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.
title: Ajout de la journalisation et du débogage en temps réel
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# Ajout de la journalisation et du débogage en temps réel{#add-real-time-logging-and-debugging}

Vous pouvez utiliser des notifications pour mettre en oeuvre la journalisation en temps réel dans votre application vidéo.

Le système de notification vous permet de collecter des informations de journalisation et de débogage pour les diagnostics et la validation sans exagérer le système.

>[!IMPORTANT]
>
>La connexion en arrière-plan ne fait pas partie d’une configuration de production et ne doit pas gérer le trafic à charge élevée. Si votre mise en oeuvre n’a pas besoin d’être absolument terminée, pensez à l’efficacité de la transmission des données pour éviter de surcharger votre système.

Voici un exemple de récupération des notifications.

1. Créez un thread d’exécution basé sur un minuteur pour votre application vidéo qui interroge périodiquement les données collectées par le système de notification TVSDK.

1. Si l’intervalle du minuteur est trop long et que la taille de la liste d’événements est trop petite, la liste d’événements de notification déborde. Pour éviter ce débordement, effectuez l’une des opérations suivantes :

   * Réduisez l’intervalle qui génère le thread qui interroge les nouveaux événements.
   * Augmentez la taille de la liste de notifications.

1. Sérialisez les dernières entrées d’événement de notification au format JSON et envoyez les entrées à un serveur distant pour le posttraitement.

   Le serveur distant peut alors afficher les données fournies sous forme graphique en temps réel.
1. Pour détecter la perte d’événements de notification, recherchez les trous dans la séquence de valeurs d’index d’événement.

   Chaque événement de notification comporte une valeur d’index automatiquement incrémentée par la variable `session.NotificationHistory` classe .

---
title: Détection de restauration
description: Détection de restauration
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---


# Détection de restauration {#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à afficher le contenu. Cet événement déclenche le début de la fenêtre de lecture. Pour appliquer de manière sécurisée la fenêtre de lecture, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer l’heure de début de la fenêtre de lecture stockée sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur de restauration du client.

Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir la variable `ClientState` , puis en appelant `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d’états client. Le serveur doit stocker cette valeur pour chaque client (utilisez `MachineId.getUniqueId()` pour identifier le client associé à la valeur de compteur de restauration, puis appelez `ClientState.incrementCounter()` pour augmenter la valeur du compteur d’une unité. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur affichée par le serveur, l’état du client peut avoir été restauré.

Voir `ClientState` Documentation de référence sur l’API pour plus d’informations sur la détection de l’horodatage de l’état client.

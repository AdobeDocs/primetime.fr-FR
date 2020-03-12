---
seo-title: Détection de restauration
title: Détection de restauration
uuid: ec124bac-a1d7-45be-bf09-a99d5eec5042
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Détection de restauration {#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à consulter le contenu pour la première fois. Ce  déclenche le de la fenêtre de lecture. Pour appliquer la fenêtre de lecture de manière sécurisée, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer le de la fenêtre de lecture  le temps stocké sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur de restauration du client.

Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir l’ `ClientState` objet, puis `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d’état client. Le serveur doit stocker cette valeur pour chaque client (à utiliser `MachineId.getUniqueId()` pour identifier le client associé à la valeur du compteur de restauration), puis appeler `ClientState.incrementCounter()` pour augmenter la valeur du compteur de 1. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur vue par le serveur, l’état du client a peut-être été rétabli.

Voir la documentation de référence `ClientState` API pour plus d’informations sur la détection des falsificateurs d’état client.

---
seo-title: Détection de restauration
title: Détection de restauration
uuid: cc554194-2848-4104-85eb-f697a86c72f2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Détection de restauration{#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à consulter le contenu pour la première fois. Ce événement déclenche le début de la fenêtre de lecture. Pour appliquer de manière sécurisée la fenêtre de lecture, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer le début de la fenêtre de lecture stocké sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur d’annulation du client. Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir l’ `ClientState` objet, puis en appelant `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d’état client. Le serveur doit stocker cette valeur pour chaque client (à utiliser `MachineId.getUniqueId()` pour identifier le client associé à la valeur du compteur d&#39;annulation), puis appeler `ClientState.incrementCounter()` pour augmenter la valeur du compteur d&#39;une unité. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur vue par le serveur, l’état du client a peut-être été rétabli. Pour plus d’informations sur la détection des falsificateurs d’état client, voir la documentation de référence `ClientState` API.

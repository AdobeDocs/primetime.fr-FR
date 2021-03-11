---
title: Détection de restauration
description: Détection de restauration
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Détection de restauration{#rollback-detection}

Pour la détection de restauration, certaines règles d’utilisation exigent que le client conserve les informations d’état pour l’application des droits. Par exemple, pour appliquer la règle d’utilisation de la fenêtre de lecture, le client stocke la date et l’heure auxquelles l’utilisateur a commencé à consulter le contenu pour la première fois. Ce événement déclenche le début de la fenêtre de lecture. Pour appliquer de manière sécurisée la fenêtre de lecture, le serveur doit s’assurer que l’utilisateur ne sauvegarde pas et ne restaure pas l’état du client afin de supprimer le début de la fenêtre de lecture stocké sur le client. Pour ce faire, le serveur effectue le suivi de la valeur du compteur d’annulation du client. Pour chaque requête, le serveur obtient la valeur du compteur en appelant `RequestMessageBase.getClientState()` pour obtenir l&#39;objet `ClientState`, puis en appelant `ClientState.getCounter()` pour obtenir la valeur actuelle du compteur d&#39;état client. Le serveur doit stocker cette valeur pour chaque client (utiliser `MachineId.getUniqueId()` pour identifier le client associé à la valeur du compteur d&#39;annulation), puis appeler `ClientState.incrementCounter()` pour augmenter la valeur du compteur de un. Si le serveur détecte que la valeur du compteur est inférieure à la dernière valeur vue par le serveur, l’état du client a peut-être été rétabli. Pour plus d&#39;informations sur la détection des falsificateurs d&#39;état client, consultez la documentation de référence de l&#39;API `ClientState`.

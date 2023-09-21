---
description: Si les règles de fonctionnement exigent que le nombre de machines pour un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les identifiants de machines associés à l’utilisateur.
title: Nombre de machines lors de l’émission de licences
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Nombre de machines lors de l’émission de licences {#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent que le nombre de machines pour un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les identifiants de machines associés à l’utilisateur.

La méthode la plus robuste pour effectuer le suivi des ID d’ordinateur consiste à stocker la valeur renvoyée par la variable [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) dans une base de données. Lors de la réception d’une nouvelle requête, comparez l’identifiant de l’ordinateur dans la requête aux identifiants d’ordinateur connus en utilisant [MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) compare les identifiants pour déterminer si les identifiants représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’identifiants d’ordinateur. Si, par exemple, cinq machines de leur domaine sont autorisées pour les utilisateurs, vous pouvez rechercher dans la base de données les identifiants de machines associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à des fins de comparaison.

Cette comparaison n’est pas pratique pour les déploiements qui autorisent un accès anonyme. Dans ce cas, [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) peut être utilisé. Cependant, cet identifiant ne peut pas être le même si l’utilisateur accède au contenu à partir des environnements d’exécution Flash et Adobe AIR®.

>[!NOTE]
>
>L’identifiant ne survit pas si l’utilisateur reformate le disque dur.
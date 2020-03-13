---
description: Si les règles de fonctionnement exigent que le nombre d’ordinateurs d’un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les ID d’ordinateur associés à l’utilisateur.
seo-description: Si les règles de fonctionnement exigent que le nombre d’ordinateurs d’un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les ID d’ordinateur associés à l’utilisateur.
seo-title: Nombre d’ordinateurs lors de l’émission des licences
title: Nombre d’ordinateurs lors de l’émission des licences
uuid: 7ba8a8d4-a31f-4f37-82a7-755cfa443544
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Nombre d’ordinateurs lors de l’émission des licences {#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent que le nombre d’ordinateurs d’un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les ID d’ordinateur associés à l’utilisateur.

La méthode la plus efficace pour suivre les ID d’ordinateur consiste à stocker la valeur renvoyée par la méthode [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) dans une base de données. Lorsqu’une nouvelle requête est reçue, comparez l’ID d’ordinateur de la requête aux ID d’ordinateur connus à l’aide de [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) effectue une comparaison des ID pour déterminer si les ID représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur. Par exemple, si les utilisateurs sont autorisés à utiliser cinq ordinateurs dans leur domaine, vous pouvez rechercher dans la base de données les ID d’ordinateur associés au nom d’utilisateur de l’utilisateur et obtenir un petit jeu de données à des fins de comparaison.

Cette comparaison n’est pas pratique pour les déploiements qui autorisent un accès anonyme. Dans ce cas, [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) peut être utilisé. Toutefois, cet ID ne peut pas être identique si l’utilisateur accède au contenu à partir des moteurs d’exécution Flash et Adobe AIR®.

>[!NOTE]
>
>L’ID ne survit pas si l’utilisateur reformate le disque dur.
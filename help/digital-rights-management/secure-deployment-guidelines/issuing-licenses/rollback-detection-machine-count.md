---
description: Si les règles de fonctionnement exigent le suivi du nombre d'ordinateurs d'un utilisateur, le serveur de licences ou le serveur de domaines doit stocker les ID d'ordinateur associés à l'utilisateur.
title: Nombre d'ordinateurs lors de l'émission des licences
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Nombre d&#39;ordinateurs lors de l&#39;émission de licences {#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent le suivi du nombre d&#39;ordinateurs d&#39;un utilisateur, le serveur de licences ou le serveur de domaines doit stocker les ID d&#39;ordinateur associés à l&#39;utilisateur.

La méthode la plus efficace pour suivre les ID d&#39;ordinateur consiste à stocker la valeur renvoyée par la méthode [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) dans une base de données. Lorsqu’une nouvelle demande est reçue, comparez l’ID d’ordinateur de la demande aux ID d’ordinateur connus en utilisant [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) effectue une comparaison des identifiants pour déterminer si les identifiants représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur. Par exemple, si les utilisateurs sont autorisés à utiliser cinq machines de leur domaine, vous pouvez rechercher dans la base de données les ID d’ordinateurs associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à des fins de comparaison.

Cette comparaison n’est pas pratique pour les déploiements qui autorisent un accès anonyme. Dans ce cas, [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) peut être utilisé. Toutefois, cet ID ne peut pas être identique si l’utilisateur accède au contenu à partir des runtimes Flash et Adobe AIR®.

>[!NOTE]
>
>L&#39;ID ne survit pas si l&#39;utilisateur reformate le disque dur.
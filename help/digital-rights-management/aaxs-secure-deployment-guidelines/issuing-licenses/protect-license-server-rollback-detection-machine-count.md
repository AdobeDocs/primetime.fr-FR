---
title: Nombre d'ordinateurs lors de l'émission des licences
description: Nombre d'ordinateurs lors de l'émission des licences
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Nombre d&#39;ordinateurs lors de l&#39;émission des licences{#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent le suivi du nombre d&#39;ordinateurs d&#39;un utilisateur, le serveur de licences ou le serveur de domaines doit stocker les ID d&#39;ordinateur associés à l&#39;utilisateur. La méthode la plus efficace pour suivre les ID d&#39;ordinateur consiste à stocker la valeur renvoyée par la méthode `MachineId.getBytes()` dans une base de données. Lorsqu&#39;une nouvelle requête arrive, comparez l&#39;ID d&#39;ordinateur de la requête aux ID d&#39;ordinateur connus en utilisant `MachineId.matches()`.

`MachineId.matches()` effectue une comparaison des identifiants pour déterminer s’ils représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur à comparer. Par exemple, si un utilisateur est autorisé à accéder à cinq ordinateurs de son domaine, vous pouvez rechercher dans la base de données les ID d’ordinateur associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à comparer.

>[!NOTE]
>
>Cette comparaison n’est pas pratique pour les déploiements permettant un accès anonyme. Dans ce cas, `MachineId.getUniqueID()` peut être utilisé, cependant, cet ID ne sera pas le même si l&#39;utilisateur accède au contenu à partir des runtimes Flash et Adobe AIR® et ne survivra pas si l&#39;utilisateur reformate son disque dur.

Pour en savoir plus sur `MachineToken.getMachineId()`et `MachineId.matches()`, consultez la *Référence de l&#39;API d&#39;accès aux Adobes*.

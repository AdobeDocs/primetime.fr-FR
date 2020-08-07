---
seo-title: Nombre d'ordinateurs lors de l'émission des licences
title: Nombre d'ordinateurs lors de l'émission des licences
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---


# Nombre d&#39;ordinateurs lors de l&#39;émission des licences{#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent le suivi du nombre d&#39;ordinateurs d&#39;un utilisateur, le serveur de licences ou le serveur de domaines doit stocker les ID d&#39;ordinateur associés à l&#39;utilisateur. La méthode la plus efficace pour suivre les ID d&#39;ordinateur consiste à stocker la valeur renvoyée par la `MachineId.getBytes()` méthode dans une base de données. Lorsqu’une nouvelle requête arrive, comparez l’ID d’ordinateur de la requête aux ID d’ordinateur connus qui utilisent `MachineId.matches()`.

`MachineId.matches()` effectue une comparaison des identifiants pour déterminer s’ils représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur à comparer. Par exemple, si un utilisateur est autorisé à accéder à cinq ordinateurs de son domaine, vous pouvez rechercher dans la base de données les ID d’ordinateur associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à comparer.

>[!NOTE]
>
>Cette comparaison n’est pas pratique pour les déploiements permettant un accès anonyme. Dans de tels cas, `MachineId.getUniqueID()` toutefois, cet ID ne sera pas le même si l’utilisateur accède au contenu à partir des runtimes Flash et Adobe AIR® et ne survivra pas si l’utilisateur reformate son disque dur.

Pour en savoir plus sur `MachineToken.getMachineId()`et `MachineId.matches()`, consultez le Guide de référence *de l&#39;API d&#39;accès* aux Adobes.

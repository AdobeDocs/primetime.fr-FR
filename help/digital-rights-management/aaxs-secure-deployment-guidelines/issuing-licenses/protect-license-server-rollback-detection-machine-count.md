---
title: Nombre de machines lors de l’émission de licences
description: Nombre de machines lors de l’émission de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Nombre de machines lors de l’émission de licences{#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent que le nombre de machines pour un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les identifiants de machines associés à l’utilisateur. La méthode la plus robuste pour effectuer le suivi des ID d’ordinateur consiste à stocker la valeur renvoyée par la variable `MachineId.getBytes()` dans une base de données. Lorsqu’une nouvelle requête arrive, comparez l’identifiant de l’ordinateur dans la requête aux identifiants d’ordinateur connus à l’aide de `MachineId.matches()`.

`MachineId.matches()` compare les identifiants afin de déterminer s’ils représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’identifiants de machine à comparer. Par exemple, si un utilisateur est autorisé à héberger cinq machines dans son domaine, vous pouvez rechercher dans la base de données les identifiants de machines associés au nom d’utilisateur de l’utilisateur et obtenir un petit ensemble de données à comparer.

>[!NOTE]
>
>Cette comparaison n’est pas pratique pour les déploiements autorisant l’accès anonyme. Dans ce cas `MachineId.getUniqueID()` peut être utilisé, cependant, cet ID ne sera pas le même si l’utilisateur accède au contenu à partir des environnements d’exécution Flash et Adobe AIR® et ne survivra pas si l’utilisateur reformate son disque dur.

Pour en savoir plus sur `MachineToken.getMachineId()`et `MachineId.matches()`, voir *Référence de l’API Adobe Access*.

---
seo-title: Nombre d’ordinateurs lors de l’émission des licences
title: Nombre d’ordinateurs lors de l’émission des licences
uuid: d57f8b0b-0363-4b26-bd71-76f4abe5b68f
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Nombre d’ordinateurs lors de l’émission des licences{#machine-count-when-issuing-licenses}

Si les règles de fonctionnement exigent que le nombre d’ordinateurs d’un utilisateur soit suivi, le serveur de licences ou le serveur de domaine doit stocker les ID d’ordinateur associés à l’utilisateur. La méthode la plus efficace pour suivre les ID d’ordinateur consiste à stocker la valeur renvoyée par la `MachineId.getBytes()` méthode dans une base de données. Lorsqu’une nouvelle requête arrive, comparez l’ID d’ordinateur de la requête aux ID d’ordinateur connus qui utilisent `MachineId.matches()`.

`MachineId.matches()` effectue une comparaison des ID pour déterminer s’ils représentent la même machine. Cette comparaison n’est pratique que s’il existe un petit nombre d’ID d’ordinateur à comparer. Par exemple, si un utilisateur est autorisé à accéder à cinq ordinateurs de son domaine, vous pouvez rechercher dans la base de données les ID d’ordinateur associés au nom d’utilisateur de l’utilisateur et obtenir un petit jeu de données à comparer.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette comparaison n’est pas pratique pour les déploiements permettant un accès anonyme. Dans ce cas, `MachineId.getUniqueID()` il est toutefois possible d’utiliser cet identifiant si l’utilisateur accède au contenu à partir des moteurs d’exécution Flash et Adobe AIR® et ne survit pas si l’utilisateur reformate son disque dur.

Pour en savoir plus `MachineToken.getMachineId()`et `MachineId.matches()`, voir le Guide de référence *des API d’accès* Adobe.

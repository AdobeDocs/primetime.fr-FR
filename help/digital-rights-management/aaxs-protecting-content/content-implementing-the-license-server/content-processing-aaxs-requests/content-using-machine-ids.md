---
title: Utilisation des identifiants de machine
description: Utilisation des identifiants de machine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Utilisation des identifiants de machine{#using-machine-identifiers}

Toutes les demandes d’accès aux Adobes (à l’exception des demandes qui prennent en charge la compatibilité FMRMS) contiennent des informations sur le jeton de machine émis au client lors de l’individualisation. Le jeton de machine contient un ID de machine, un identifiant attribué lors de l’individualisation. Utilisez cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

L’identifiant peut être utilisé de deux manières différentes. La variable `getUniqueId()` renvoie une chaîne attribuée à l’appareil lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant change si l’utilisateur reformate le disque dur et s’individualise à nouveau. Cet identifiant aura également une valeur différente entre Adobe® AIR® et Adobe® Flash® Player dans différents navigateurs sur le même ordinateur.

Pour comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant entier. Pour déterminer si la machine a déjà été vue, récupérez tous les identifiants pour un nom d’utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Parce que la variable `matches()` doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n’est pratique que s’il existe un petit nombre de valeurs à comparer (par exemple, les machines associées à un utilisateur particulier).

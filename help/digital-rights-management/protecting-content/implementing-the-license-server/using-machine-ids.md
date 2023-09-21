---
title: Utilisation des identifiants de machine
description: Utilisation des identifiants de machine
copied-description: true
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Utilisation des identifiants de machine{#use-machine-identifiers}

Toutes les demandes Adobe Primetime DRM (à l’exception des demandes qui prennent en charge la compatibilité FMRMS) incluent des informations sur le jeton de la machine qui a été émis au client lors de l’individualisation. Le jeton de machine comprend un ID de machine, qui est un identifiant attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La variable `getUniqueId()` renvoie une chaîne qui a été affectée à un appareil lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant change si l’utilisateur reformate le disque dur et s’individualise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Adobe Flash Player dans différents navigateurs sur le même ordinateur.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant entier. Pour déterminer si la machine a déjà été vue, récupérez tous les identifiants pour un nom d’utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Parce que la variable `matches()` doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n’est pratique que s’il existe un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.


---
seo-title: Utiliser des identifiants de machine
title: Utiliser des identifiants de machine
uuid: 14eee414-62f1-4a9d-84bd-689ca2271d19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Utiliser les identifiants de machine{#use-machine-identifiers}

Toutes les demandes Adobe Primetime DRM (à l’exception des demandes qui prennent en charge la compatibilité FMRMS) incluent des informations sur le jeton machine qui ont été émises au client lors de l’individualisation. Le jeton machine comprend un ID machine, qui est un identifiant attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour comptabiliser le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La méthode `getUniqueId()` renvoie une chaîne qui a été attribuée à un périphérique lors de l&#39;individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant change si l&#39;utilisateur reformate le disque dur et se individualise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Flash Player d’Adobe dans différents navigateurs sur la même machine.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l&#39;identifiant complet. Pour déterminer si l&#39;ordinateur a été vu auparavant, obtenez tous les identifiants pour un nom d&#39;utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Étant donné que la méthode `matches()` doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n&#39;est pratique que lorsqu&#39;il y a un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.


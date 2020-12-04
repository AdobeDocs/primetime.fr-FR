---
seo-title: Utilisation des identifiants de machine
title: Utilisation des identifiants de machine
uuid: 2832c158-fade-4bbf-ae89-f95ce9dfc369
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Utilisation des identifiants de machine{#using-machine-identifiers}

Toutes les demandes d&#39;accès à l&#39;Adobe (à l&#39;exception des demandes qui prennent en charge la compatibilité FMRMS) contiennent des informations sur le jeton machine émis au client lors de l&#39;individualisation. Le jeton machine contient un ID machine, un identifiant attribué lors de l’individualisation. Utilisez cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou rejoint un domaine.

Il existe deux façons d’utiliser l’identifiant. La méthode `getUniqueId()` renvoie une chaîne attribuée au périphérique lors de l&#39;individualisation. Vous pouvez stocker les chaînes dans une base de données et les rechercher par identifiant. Cependant, cet identifiant changera si l&#39;utilisateur reformate le disque dur et s&#39;individualise à nouveau. Cet identifiant aura également une valeur différente entre Adobe® AIR® et Adobe® Flash® Player dans différents navigateurs sur la même machine.

Pour comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l&#39;identifiant complet. Pour déterminer si l&#39;ordinateur a été vu auparavant, obtenez tous les identifiants pour un nom d&#39;utilisateur et appelez `matches()` pour vérifier si une correspondance est trouvée. Comme la méthode `matches()` doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n&#39;est pratique que lorsqu&#39;il existe un petit nombre de valeurs à comparer (par exemple, les machines associées à un utilisateur particulier).

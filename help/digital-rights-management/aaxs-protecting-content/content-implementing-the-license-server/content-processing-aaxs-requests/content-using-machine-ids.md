---
seo-title: Utilisation des identifiants de machine
title: Utilisation des identifiants de machine
uuid: 2832c158-fade-4bbf-ae89-f95ce9dfc369
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utilisation des identifiants de machine{#using-machine-identifiers}

Toutes les requêtes Adobe Access (à l’exception des requêtes prenant en charge la compatibilité FMRMS) contiennent des informations sur le jeton machine émis au client lors de l’individualisation. Le jeton machine contient un ID machine, un identifiant attribué lors de l’individualisation. Utilisez cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou rejoint un domaine.

Il existe deux façons d’utiliser l’identifiant. La `getUniqueId()` méthode renvoie une chaîne attribuée au périphérique lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et effectuer une recherche par identifiant. Cependant, cet identifiant change si l&#39;utilisateur reformate le disque dur et le personnalise à nouveau. Cet identifiant aura également une valeur différente entre Adobe® AIR® et Adobe® Flash® Player dans différents navigateurs sur le même ordinateur.

Pour comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant complet. Pour déterminer si l’ordinateur a déjà été vu, obtenez tous les identifiants d’un nom d’utilisateur et appelez `matches()` pour vérifier si une correspondance est possible. Comme la `matches()` méthode doit être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n’est pratique que lorsqu’il existe un petit nombre de valeurs à comparer (par exemple, les machines associées à un utilisateur particulier).

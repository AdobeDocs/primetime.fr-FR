---
seo-title: Utiliser des identifiants de machine
title: Utiliser des identifiants de machine
uuid: 14eee414-62f1-4a9d-84bd-689ca2271d19
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Utiliser des identifiants de machine{#use-machine-identifiers}

Toutes les demandes DRM Adobe Primetime (à l’exception des demandes prenant en charge la compatibilité FMRMS) incluent des informations sur le jeton d’ordinateur qui a été émis au client lors de l’individualisation. Le jeton de l’ordinateur comprend un ID d’ordinateur, identifiant qui a été attribué lors de l’individualisation. Vous pouvez utiliser cet identifiant pour compter le nombre de machines à partir desquelles un utilisateur a demandé une licence ou a rejoint un domaine.

Vous pouvez utiliser un identifiant comme suit :

* La `getUniqueId()` méthode renvoie une chaîne qui a été affectée à un périphérique lors de l’individualisation. Vous pouvez stocker les chaînes dans une base de données et effectuer une recherche par identifiant. Toutefois, cet identifiant change si l’utilisateur reformate le disque dur et le personnalise à nouveau. Cet identifiant a également une valeur différente entre Adobe AIR et Adobe Flash Player dans différents navigateurs sur le même ordinateur.
* Si vous souhaitez comptabiliser plus précisément les machines, vous pouvez utiliser `getBytes()` pour stocker l’identifiant complet. Pour déterminer si l’ordinateur a déjà été vu, obtenez tous les identifiants d’un nom d’utilisateur et appelez `matches()` pour vérifier si une correspondance est possible. La `matches()` méthode devant être utilisée pour comparer les valeurs renvoyées par `MachineId.getBytes`, cette option n&#39;est pratique que lorsqu&#39;il existe un petit nombre de valeurs à comparer ; par exemple, les machines associées à un utilisateur particulier.


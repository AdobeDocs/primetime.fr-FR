---
title: Domaines anonymes
description: Domaines anonymes
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Domaines anonymes {#anonymous-domains}

Dans ce cas pratique, un grand nombre d’appareils appartiennent à un seul domaine et l’authentification peut ne pas être requise. Pour utiliser ce type de domaine avec l’implémentation de référence, créez la stratégie spécifiant que l’enregistrement de domaine est requis. Spécifiez l’URL du serveur de domaine comme `https:// host:port/flashaccess/domainserver/domainname/` et indiquez l’authentification anonyme.

L’implémentation de référence met en oeuvre la logique suivante pour l’enregistrement de domaine :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans le `DomainServerInfo` table. Si aucune entrée n&#39;est trouvée, insérez une entrée dans le tableau (valeurs par défaut : l&#39;authentification n&#39;est pas requise et aucun nombre maximum d&#39;appartenance).
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la requête et qu’il correspond à l’espace de noms Auth, s’il est spécifié dans la base de données.

   1. Si une authentification est requise, mais qu’aucun jeton d’authentification valide n’a été fourni, renvoie une erreur `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Vérifiez si le périphérique s’est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans le `DomainMembership` table. Pour chaque GUID de machine trouvé, comparez-le au GUID de machine dans la requête. S’il s’agit d’une nouvelle machine, ajoutez une entrée au `DomainMembership` table.

   1. S’il s’agit d’un nouvel appareil, l’appartenance maximale a déjà été atteinte, renvoie une erreur. `DOM_LIMIT_REACHED (502)`.

1. Recherchez toutes les clés de domaine pour ce domaine dans le `DomainKeys` table.

   1. If `DomainServerInfo` indique que les clés doivent être roulées, générez une nouvelle paire de clés, enregistrez-la dans la variable `DomainKeys` (avec la version de clé 1 supérieure à la clé existante la plus élevée), et réinitialisez la variable `Key Rollover Required` indicateur dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence met en oeuvre la logique suivante pour le désenregistrement de domaine :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans le `DomainServerInfo` table.
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la requête et qu’il correspond à l’espace de noms Auth, s’il est spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID de l’ordinateur dans le `DomainMembership` table. Si une entrée correspondante est introuvable, erreur de retour `DEREG_DENIED (401)`.

1. S’il ne s’agit pas d’une demande d’aperçu, supprimez l’entrée de `DomainMembership` et définissez la variable `Key Rollover Required` indicateur dans `DomainServerInfo`.

Dans ce cas pratique, puisqu’un grand nombre de machines peuvent rejoindre le domaine, il n’est pas possible de faire entièrement correspondre l’identifiant de la machine. À la place, le GUID de machine aléatoire affecté à la machine lors de l’individualisation est utilisé.

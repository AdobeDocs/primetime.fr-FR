---
seo-title: Domaines anonymes
title: Domaines anonymes
uuid: ee29ae4d-65b2-48de-b441-18c8cf55de32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Domaines anonymes {#anonymous-domains}

Dans ce cas d’utilisation, un grand nombre de périphériques appartiennent à un seul domaine et l’authentification peut ne pas être requise. Pour utiliser ce type de domaine avec l’implémentation des références, créez la stratégie spécifiant que l’enregistrement du domaine est obligatoire. Spécifiez l’URL du serveur de domaine comme [*!DNL https:// host:port/flashaccess/domainserver/domainname/*] et l’authentification anonyme.

L’implémentation de référence implémente la logique suivante pour l’enregistrement de domaine :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans le `DomainServerInfo` tableau. Si une entrée est introuvable, insérez une entrée dans le tableau (valeurs par défaut : l’authentification n’est pas obligatoire et aucun abonnement maximum).
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la requête et qu’il correspond au  Auth , s’il est spécifié dans la base de données.

   1. Si l’authentification est requise mais qu’aucun jeton d’authentification valide n’a été fourni, l’erreur de renvoi `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Vérifiez si le périphérique est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans le `DomainMembership` tableau. Pour chaque GUID d’ordinateur trouvé, comparez-le au GUID d’ordinateur dans la requête. S’il s’agit d’une nouvelle machine, ajoutez une entrée au `DomainMembership` tableau.

   1. S&#39;il s&#39;agit d&#39;un nouvel appareil et que l&#39;abonnement maximum a déjà été atteint, renvoie une erreur `DOM_LIMIT_REACHED (502)`.

1. Recherchez toutes les clés de domaine de ce domaine dans le `DomainKeys` tableau.

   1. Si `DomainServerInfo` indique que les clés doivent être survolées, générez une nouvelle paire de clés, enregistrez-la dans le `DomainKeys` tableau (avec la version de clé 1 supérieure à la clé existante la plus élevée), puis réinitialisez l’ `Key Rollover Required` indicateur dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence implémente la logique suivante pour le désenregistrement de domaine :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans le `DomainServerInfo` tableau.
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la requête et qu’il correspond au  Auth , s’il est spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID de l’ordinateur dans le `DomainMembership` tableau. Si une entrée correspondante est introuvable, renvoie une erreur `DEREG_DENIED (401)`.

1. S’il ne s’agit pas d’une demande de , supprimez l’entrée `DomainMembership` et définissez l’ `Key Rollover Required` indicateur dans `DomainServerInfo`.

Dans ce cas d’utilisation, puisqu’un grand nombre d’ordinateurs peuvent rejoindre le domaine, il n’est pas possible de faire correspondre complètement l’ID d’ordinateur. Le GUID de machine aléatoire attribué à la machine lors de l’individualisation est utilisé.

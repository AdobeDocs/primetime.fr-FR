---
seo-title: Domaines anonymes
title: Domaines anonymes
uuid: ee29ae4d-65b2-48de-b441-18c8cf55de32
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Domaines anonymes {#anonymous-domains}

Dans ce cas d’utilisation, un grand nombre de périphériques appartiennent à un seul domaine et l’authentification peut ne pas être requise. Pour utiliser ce type de domaine avec l’implémentation des références, créez la stratégie spécifiant que l’enregistrement du domaine est requis. Spécifiez l’URL du serveur de domaine en tant que [*!DNL https:// host:port/flashaccess/domainserver/domainname/*] et l’authentification anonyme.

L’implémentation de référence implémente la logique suivante pour l’enregistrement de domaine :

1. Analyse le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans le `DomainServerInfo` tableau. Si une entrée est introuvable, insérez-la dans la table (valeurs par défaut : l’authentification n’est pas requise et aucun abonnement maximum).
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la demande et qu’il correspond à l’Espace de nommage d’authentification, s’il est spécifié dans la base de données.

   1. Si une authentification est requise mais qu’aucun jeton d’authentification valide n’a été fourni, l’erreur de renvoi `DOM_AUTHENTICATION_REQUIRED (503)`.

1. Vérifiez si le périphérique s’est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans le `DomainMembership` tableau. Pour chaque GUID d&#39;ordinateur trouvé, comparez avec le GUID d&#39;ordinateur dans la requête. S&#39;il s&#39;agit d&#39;une nouvelle machine, ajoutez une entrée à la `DomainMembership` table.

   1. S&#39;il s&#39;agit d&#39;un nouveau périphérique et que l&#39;adhésion maximale a déjà été atteinte, une erreur de retour `DOM_LIMIT_REACHED (502)`.

1. Recherchez toutes les clés de domaine de ce domaine dans le `DomainKeys` tableau.

   1. Si `DomainServerInfo` indique que les clés doivent être roulées, générez une nouvelle paire de clés, enregistrez-la dans la `DomainKeys` table (avec la version de clé une plus élevée que la clé existante la plus élevée), et réinitialisez l&#39; `Key Rollover Required` indicateur dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence implémente la logique suivante pour le désenregistrement de domaine :

1. Analyse le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans la `DomainServerInfo` table.
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la demande et qu’il correspond à l’Espace de nommage d’authentification, s’il est spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID de l&#39;ordinateur dans le `DomainMembership` tableau. Si une entrée correspondante est introuvable, renvoie une erreur `DEREG_DENIED (401)`.

1. S’il ne s’agit pas d’une demande de prévisualisation, supprimez l’entrée `DomainMembership` et définissez l’ `Key Rollover Required` indicateur dans `DomainServerInfo`.

Dans ce cas d’utilisation, puisqu’un grand nombre d’ordinateurs peuvent rejoindre le domaine, il n’est pas possible de faire correspondre entièrement l’ID de l’ordinateur. Au lieu de cela, le GUID de machine aléatoire attribué à la machine pendant l&#39;individualisation est utilisé.

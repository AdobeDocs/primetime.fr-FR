---
seo-title: Domaines anonymes
title: Domaines anonymes
uuid: ee29ae4d-65b2-48de-b441-18c8cf55de32
translation-type: tm+mt
source-git-commit: 4f196bbd079edeb1a423afee6b4b7e249d380f40
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Domaines anonymes {#anonymous-domains}

Dans ce cas d’utilisation, un grand nombre de périphériques appartiennent à un seul domaine et l’authentification peut ne pas être requise. Pour utiliser ce type de domaine avec l’implémentation des références, créez la stratégie spécifiant que l’enregistrement du domaine est requis. Spécifiez l’URL du serveur de domaine `https:// host:port/flashaccess/domainserver/domainname/` et l’authentification anonyme.

L’implémentation de référence implémente la logique suivante pour l’enregistrement de domaine :

1. Analyse le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans la table `DomainServerInfo`. Si une entrée est introuvable, insérez-la dans la table (valeurs par défaut : l’authentification n’est pas requise et aucun abonnement maximum).
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la demande et qu’il correspond à l’Espace de nommage d’authentification, s’il est spécifié dans la base de données.

   1. Si l&#39;authentification est requise mais qu&#39;aucun jeton d&#39;authentification valide n&#39;a été fourni, l&#39;erreur de renvoi `DOM_AUTHENTICATION_REQUIRED (503)` est renvoyée.

1. Vérifiez si le périphérique s’est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans la table `DomainMembership`. Pour chaque GUID d&#39;ordinateur trouvé, comparez avec le GUID d&#39;ordinateur dans la requête. S&#39;il s&#39;agit d&#39;un nouvel ordinateur, ajoutez une entrée à la table `DomainMembership`.

   1. S&#39;il s&#39;agit d&#39;un nouveau périphérique et que l&#39;adhésion maximale a déjà été atteinte, l&#39;erreur de renvoi `DOM_LIMIT_REACHED (502)` est renvoyée.

1. Recherchez toutes les clés de domaine pour ce domaine dans la table `DomainKeys`.

   1. Si `DomainServerInfo` indique que les clés doivent être reportées, générez une nouvelle paire de clés, enregistrez-la dans la table `DomainKeys` (avec la version de clé 1 supérieure à la clé existante la plus élevée), et réinitialisez l&#39;indicateur `Key Rollover Required` dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence implémente la logique suivante pour le désenregistrement de domaine :

1. Analyse le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans la table `DomainServerInfo`.
1. Si l’authentification est requise pour le domaine demandé, assurez-vous qu’un jeton d’authentification valide a été inclus dans la demande et qu’il correspond à l’Espace de nommage d’authentification, s’il est spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID d&#39;ordinateur dans la table `DomainMembership`. Si une entrée correspondante est introuvable, renvoie une erreur `DEREG_DENIED (401)`.

1. S&#39;il ne s&#39;agit pas d&#39;une demande de prévisualisation, supprimez l&#39;entrée de `DomainMembership` et définissez l&#39;indicateur `Key Rollover Required` dans `DomainServerInfo`.

Dans ce cas d’utilisation, puisqu’un grand nombre d’ordinateurs peuvent rejoindre le domaine, il n’est pas possible de faire correspondre entièrement l’ID de l’ordinateur. Au lieu de cela, le GUID de machine aléatoire attribué à la machine pendant l&#39;individualisation est utilisé.

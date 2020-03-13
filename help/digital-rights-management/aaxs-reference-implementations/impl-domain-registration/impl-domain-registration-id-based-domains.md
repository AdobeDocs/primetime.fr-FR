---
seo-title: Domaines basés sur l’identité
title: Domaines basés sur l’identité
uuid: 34cad19b-1adb-4e0c-ac59-50632f6988f7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Domaines basés sur l’identité {#identity-based-domains}

Dans ce cas d’utilisation, chaque utilisateur authentifié possède son propre domaine et un certain nombre de périphériques sont autorisés à le rejoindre. Pour utiliser ce type de domaine avec l’implémentation des références, créez une stratégie spécifiant que l’enregistrement des domaines est requis. Spécifiez l’hôte et le port de votre serveur pour l’URL du serveur de domaine et indiquez que l’authentification du nom d’utilisateur/mot de passe est requise.

L’implémentation de référence implémente la logique suivante pour l’enregistrement de domaine :

1. Déterminez le nom de domaine à affecter à cet utilisateur. Le nom de domaine sera * `namequalifier:username`* extrait du jeton d’authentification. S’il n’existe aucun jeton d’authentification, renvoyez l’erreur DOM_AUTHENTICATION_REQUIRED (503).
1. Recherchez le nom de domaine dans le `DomainServerInfo` tableau. Si aucune entrée n’est trouvée, insérez une entrée dans le tableau (les valeurs par défaut sont l’authentification requise, l’appartenance au domaine max. = 5).
1. Vérifiez si le périphérique est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans la `UserDomainMembership` table. Pour chaque ID d’ordinateur trouvé, comparez-le à l’ID d’ordinateur dans la requête. S’il s’agit d’une nouvelle machine, ajoutez une entrée au `UserDomainMembership` tableau. Recherchez ensuite les enregistrements correspondants dans la `UserDomainRefCount` table. Si aucune entrée n’existe pour ce GUID d’ordinateur, ajoutez un enregistrement.

   1. S&#39;il s&#39;agit d&#39;un nouveau périphérique et que l&#39;adhésion maximale a déjà été atteinte, l&#39;erreur DOM_LIMIT_REACHED (502) est renvoyée.

1. Recherchez toutes les clés de domaine de ce domaine dans la table DomainKeys.

   1. Si `DomainServerInfo` indique que les clés doivent être survolées, générez une nouvelle paire de clés, enregistrez-la dans le `DomainKeys` tableau (avec la version de clé 1 supérieure à la clé existante la plus élevée), puis réinitialisez l’indicateur &quot;Survol de clé requis&quot; dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence met en oeuvre la logique suivante pour le désenregistrement de domaine :

1. Déterminez le nom de domaine à affecter à cet utilisateur. Le nom de domaine sera *namequalifier:username* extrait du jeton d’authentification. S’il n’existe aucun jeton d’authentification, renvoyez l’erreur DOM_AUTHENTICATION_REQUIRED (503).
1. Recherchez le nom de domaine demandé dans le `DomainServerInfo` tableau.
1. Recherchez le nom de domaine dans le `UserDomainMembership` tableau. Pour chaque ID d’ordinateur trouvé, comparez-le à l’ID d’ordinateur dans la requête. Recherchez l’entrée correspondante dans le `UserDomainRefCount` tableau. Si une entrée correspondante est introuvable, l’erreur de renvoi DEREG_DENIED (401) est renvoyée.

1. S’il ne s’agit pas d’une requête de , supprimez l’entrée de la `UserDomainRefCount` table. S’il n’y a plus d’entrées dans cette table pour l’ordinateur, supprimez l’entrée de `UserDomainMembership` et définissez l’indicateur &quot;Survol de clé requis&quot; dans `DomainServerInfo`.

Dans ce cas d&#39;utilisation, chaque utilisateur est autorisé à enregistrer un petit nombre de machines, de sorte que nous pouvons utiliser l&#39;ID d&#39;ordinateur complet et la `matches()` méthode pour comptabiliser correctement les machines. Toutefois, comme l’utilisateur peut s’enregistrer plusieurs fois sur cet ordinateur (par le biais de plusieurs applications AIR ou de lecteurs dans différents navigateurs), le serveur doit également conserver un nombre de références afin que la désinscription puisse être comptabilisée avec précision. Le désenregistrement ne peut pas être considéré comme terminé tant que tous les jetons de domaine de l’ordinateur ne sont pas rendus.

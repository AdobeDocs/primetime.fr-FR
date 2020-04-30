---
seo-title: Domaines basés sur l’identité
title: Domaines basés sur l’identité
uuid: 34cad19b-1adb-4e0c-ac59-50632f6988f7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Domaines basés sur l’identité {#identity-based-domains}

Dans ce cas d’utilisation, chaque utilisateur authentifié possède son propre domaine et un certain nombre de périphériques sont autorisés à le rejoindre. Pour utiliser ce type de domaine avec l’implémentation des références, créez une stratégie spécifiant l’enregistrement des domaines. Spécifiez l’hôte et le port de votre serveur pour l’URL du serveur de domaine et indiquez que l’authentification du nom d’utilisateur/mot de passe est requise.

L’implémentation de référence implémente la logique suivante pour l’enregistrement de domaine :

1. Déterminez le nom de domaine à attribuer à cet utilisateur. Le nom de domaine sera * `namequalifier:username`* extrait du jeton d’authentification. S’il n’existe aucun jeton d’authentification, renvoyez l’erreur DOM_AUTHENTICATION_REQUIRED (503).
1. Recherchez le nom de domaine dans le `DomainServerInfo` tableau. Si aucune entrée n&#39;est trouvée, insérez une entrée dans la table (les valeurs par défaut sont l&#39;authentification requise, l&#39;adhésion au domaine max=5).
1. Vérifiez si le périphérique s’est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans la `UserDomainMembership` table. Pour chaque ID d’ordinateur trouvé, comparez-le à l’ID d’ordinateur dans la requête. S&#39;il s&#39;agit d&#39;une nouvelle machine, ajoutez une entrée à la `UserDomainMembership` table. Recherchez ensuite les enregistrements correspondants dans la `UserDomainRefCount` table. Si une entrée n&#39;existe pas pour ce GUID d&#39;ordinateur, ajoutez un enregistrement.

   1. S&#39;il s&#39;agit d&#39;un nouveau périphérique et que l&#39;adhésion maximale a déjà été atteinte, l&#39;erreur de renvoi DOM_LIMIT_REACHED (502).

1. Recherchez toutes les clés de domaine de ce domaine dans la table DomainKeys.

   1. Si `DomainServerInfo` indique que les clés doivent être roulées, générez une nouvelle paire de clés, enregistrez-la dans la `DomainKeys` table (avec la version de clé une plus élevée que la clé existante la plus élevée), et réinitialisez l&#39;indicateur &quot;Survol de clé requis&quot; dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence met en oeuvre la logique suivante pour le désenregistrement de domaine :

1. Déterminez le nom de domaine à attribuer à cet utilisateur. Le nom de domaine sera *namequalifier:username* extrait du jeton d’authentification. S’il n’existe aucun jeton d’authentification, renvoyez l’erreur DOM_AUTHENTICATION_REQUIRED (503).
1. Recherchez le nom de domaine demandé dans la `DomainServerInfo` table.
1. Recherchez le nom de domaine dans le `UserDomainMembership` tableau. Pour chaque ID d’ordinateur trouvé, comparez-le à l’ID d’ordinateur dans la requête. Recherchez l&#39;entrée correspondante dans le `UserDomainRefCount` tableau. Si une entrée correspondante est introuvable, l&#39;erreur de renvoi DEREG_DENIED (401) est renvoyée.

1. S&#39;il ne s&#39;agit pas d&#39;une demande de prévisualisation, supprimez l&#39;entrée de la `UserDomainRefCount` table. S&#39;il n&#39;y a plus d&#39;entrées dans cette table pour l&#39;ordinateur, supprimez l&#39;entrée `UserDomainMembership` et définissez l&#39;indicateur &quot;Survol clé requis&quot; dans `DomainServerInfo`.

Dans ce cas d&#39;utilisation, chaque utilisateur est autorisé à enregistrer un petit nombre d&#39;ordinateurs, de sorte que nous pouvons utiliser l&#39;ID d&#39;ordinateur complet et la `matches()` méthode pour comptabiliser correctement les machines. Cependant, puisque l’utilisateur peut s’enregistrer plusieurs fois sur cet ordinateur (par le biais de plusieurs applications AIR ou de lecteurs dans différents navigateurs), le serveur doit également conserver un nombre de références, afin que la désinscription puisse être comptabilisée avec précision. Le désenregistrement ne peut pas être considéré comme terminé tant que tous les jetons de domaine de l’ordinateur ne sont pas restitués.

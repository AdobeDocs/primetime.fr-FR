---
title: Domaines basés sur les identités
description: Domaines basés sur les identités
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Domaines basés sur les identités {#identity-based-domains}

Dans ce cas pratique, chaque utilisateur authentifié possède son propre domaine et un certain nombre d’appareils sont autorisés à le rejoindre. Pour utiliser ce type de domaine avec l’implémentation de référence, créez une stratégie spécifiant que l’enregistrement de domaine est requis. Indiquez l’hôte et le port de votre serveur pour l’URL du serveur de domaine et indiquez que l’authentification par nom d’utilisateur/mot de passe est requise.

L’implémentation de référence met en oeuvre la logique suivante pour l’enregistrement de domaine :

1. Déterminez le nom de domaine à affecter à cet utilisateur. Le nom de domaine sera * `namequalifier:username`* extrait du jeton d’authentification. S’il n’existe aucun jeton d’authentification, renvoie l’erreur DOM_AUTHENTICATION_REQUIRED (503).
1. Recherchez le nom de domaine dans le `DomainServerInfo` table. Si aucune entrée n’est trouvée, insérez une entrée dans le tableau (les valeurs par défaut sont une authentification requise, nombre maximal d’appartenance à un domaine = 5).
1. Vérifiez si le périphérique s’est déjà enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans le `UserDomainMembership` table. Pour chaque ID d’ordinateur trouvé, comparez-le à l’ID d’ordinateur dans la requête. S’il s’agit d’une nouvelle machine, ajoutez une entrée au `UserDomainMembership` table. Recherchez ensuite les enregistrements correspondants dans `UserDomainRefCount` table. Si aucune entrée n’existe pour ce GUID de machine, ajoutez un enregistrement.

   1. S’il s’agit d’un nouvel appareil et que l’appartenance maximale a déjà été atteinte, l’erreur DOM_LIMIT_REACHED (502) est renvoyée.

1. Recherchez toutes les clés de domaine pour ce domaine dans la table DomainKeys .

   1. If `DomainServerInfo` indique que les clés doivent être roulées, générez une nouvelle paire de clés, enregistrez-la dans la variable `DomainKeys` (avec la version de clé une supérieure à la clé existante la plus élevée), et réinitialisez l’indicateur &quot;Survol de clé requis&quot; dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

L’implémentation de référence met en oeuvre la logique suivante pour le désenregistrement de domaine :

1. Déterminez le nom de domaine à affecter à cet utilisateur. Le nom de domaine sera *namequalifier:username* extrait du jeton d’authentification. S’il n’existe aucun jeton d’authentification, renvoie l’erreur DOM_AUTHENTICATION_REQUIRED (503).
1. Recherchez le nom de domaine demandé dans le `DomainServerInfo` table.
1. Recherchez le nom de domaine dans le `UserDomainMembership` table. Pour chaque ID d’ordinateur trouvé, comparez-le à l’ID d’ordinateur dans la requête. Recherchez l’entrée correspondante dans la `UserDomainRefCount` table. Si une entrée correspondante est introuvable, renvoie l’erreur DEREG_DENIED (401).

1. S’il ne s’agit pas d’une demande d’aperçu, supprimez l’entrée de `UserDomainRefCount` table. S’il n’y a plus d’entrées dans cette table pour la machine, supprimez l’entrée de `UserDomainMembership` et définissez l’indicateur &quot;Survol de clé requis&quot; dans `DomainServerInfo`.

Dans ce cas d’utilisation, chaque utilisateur est autorisé à enregistrer un petit nombre de machines afin que nous puissions utiliser l’identifiant complet de l’ordinateur et le `matches()` pour comptabiliser précisément les machines. Cependant, comme l’utilisateur peut s’enregistrer plusieurs fois sur cet ordinateur (par le biais de plusieurs applications AIR ou de lecteurs dans différents navigateurs), le serveur doit également maintenir un nombre de références, de sorte que la désinscription puisse être comptabilisée avec précision. La désinscription ne peut pas être considérée comme terminée tant que tous les jetons de domaine de l’ordinateur ne sont pas restitués.

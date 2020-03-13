---
description: 'null'
seo-description: 'null'
seo-title: Logique d'enregistrement de domaine basée sur l'identité
title: Logique d'enregistrement de domaine basée sur l'identité
uuid: bc13f7c2-9a20-4f80-b96f-05f7a0fcc343
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Logique d&#39;enregistrement de domaine basée sur l&#39;identité{#identity-based-domain-registration-logic}

## Logique d&#39;enregistrement de domaine {#section_149C247458954877AF158B4A09A8526B}

L’implémentation de référence applique la logique suivante pour l’enregistrement de domaine basé sur l’identité :

1. Déterminez le nom de domaine à affecter à un utilisateur désigné.

   Le nom de domaine ( `namequalifier:username`) est extrait du jeton d’authentification. Si aucun jeton n’est disponible, une erreur est générée.
1. Recherchez le nom de domaine dans la `DomainServerInfo` table.

   Si aucune entrée n’est trouvée, insérez une entrée. Les valeurs par défaut sont les suivantes :

   * `authentication required`
   * `max domain membership=5`
   .

1. Pour vérifier que le périphérique a été enregistré avec le domaine :

   1. Recherchez la `domainname` table `UserDomainMembership` :

      1. Pour chaque ID d’ordinateur situé, comparez l’ID à l’ID d’ordinateur dans la requête.
      1. S’il s’agit d’une nouvelle machine, ajoutez une entrée au `UserDomainMembership` tableau.
      1. Recherchez les enregistrements correspondants dans la `UserDomainRefCount` table.
      1. Si aucune entrée n’existe pour ce GUID d’ordinateur, ajoutez un enregistrement.
   1. S’il s’agit d’un nouveau périphérique et que la `Max Membership` valeur a été atteinte, renvoie une erreur.


1. Recherchez toutes les clés de domaine de ce domaine dans le `DomainKeys` tableau :

   1. Si `DomainServerInfo` indique que les clés doivent être survolées, générez une nouvelle paire de clés,
   1. Enregistrez la paire dans le `DomainKeys` tableau, avec une version de clé supérieure à la clé existante la plus élevée.
   1. Réinitialisez le `Key Rollover Required` drapeau dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

## Logique de désenregistrement de domaine {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

L’implémentation de référence applique la logique suivante pour le désenregistrement de domaine basé sur l’identité :

1. Déterminez le nom de domaine à affecter à cet utilisateur.

   Le nom de domaine est `namequalifier:username`, qui est extrait du jeton d’authentification. Si aucun jeton n’est disponible, une erreur de renvoi `DOM_AUTHENTICATION_REQUIRED (503)` se produit.
1. Recherchez le nom de domaine demandé dans la `DomainServerInfo` table.
1. Recherchez le nom de domaine dans la `UserDomainMembership` table.
1. Comparez chaque ID d’ordinateur trouvé avec l’ID d’ordinateur dans la requête.
1. Localisez l’entrée correspondante dans le `UserDomainRefCount` tableau.

   Si aucune entrée correspondante n’est trouvée, renvoie une erreur.

1. S’il ne s’agit pas d’une demande de , supprimez l’entrée du `UserDomainRefCount` tableau.
1. S’il n’y a pas d’entrées supplémentaires dans cette table pour l’ordinateur, supprimez l’entrée `UserDomainMembership` et définissez l’ [!DNL Key Rollover Required] indicateur dans la `DomainServerInfo` propriété.

Chaque utilisateur peut enregistrer un petit nombre d&#39;ordinateurs, de sorte que vous puissiez utiliser l&#39;ID d&#39;ordinateur complet et la `matches()` méthode pour comptabiliser les ordinateurs. Un utilisateur pouvant s’enregistrer plusieurs fois, par le biais de plusieurs applications AIR ou de lecteurs dans différents navigateurs, le serveur doit conserver un nombre de références afin que la désinscription puisse également être comptabilisée.

>[!NOTE]
>
>La désinscription n’est pas terminée tant que tous les jetons de domaine de l’ordinateur ne sont pas rendus.


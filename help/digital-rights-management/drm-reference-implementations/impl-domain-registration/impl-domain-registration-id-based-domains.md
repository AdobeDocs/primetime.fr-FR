---
title: Logique d’enregistrement des domaines basée sur les identités
description: Logique d’enregistrement des domaines basée sur les identités
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Logique d’enregistrement des domaines basée sur les identités{#identity-based-domain-registration-logic}

## Logique d’enregistrement des domaines {#section_149C247458954877AF158B4A09A8526B}

L’implémentation de référence applique la logique suivante pour l’enregistrement de domaine basé sur l’identité :

1. Déterminez le nom de domaine à affecter à un utilisateur désigné.

   Le nom de domaine ( `namequalifier:username`) est extrait du jeton d’authentification. Si aucun jeton n’est disponible, une erreur est générée.
1. Recherchez le nom de domaine dans le `DomainServerInfo` table.

   Si aucune entrée n’est trouvée, insérez une entrée. Les valeurs par défaut sont les suivantes :

   * `authentication required`
   * `max domain membership=5`

   .

1. Pour vérifier que le périphérique a été enregistré sur le domaine :

   1. Recherchez la variable `domainname` dans le `UserDomainMembership` table :

      1. Pour chaque ID d’ordinateur qui se trouve, comparez-le à l’ID d’ordinateur dans la requête.
      1. S’il s’agit d’une nouvelle machine, ajoutez une entrée au `UserDomainMembership` table.
      1. Recherchez les enregistrements correspondants dans `UserDomainRefCount` table.
      1. Si aucune entrée n’existe pour ce GUID de machine, ajoutez un enregistrement.

   1. S’il s’agit d’un nouvel appareil, et la variable `Max Membership` a été atteinte, erreur de retour .

1. Recherchez toutes les clés de domaine pour ce domaine dans le `DomainKeys` table :

   1. If `DomainServerInfo` indique que les clés doivent être roulées, générer une nouvelle paire de clés,
   1. Enregistrez la paire dans le `DomainKeys` avec une version de clé supérieure à la clé existante la plus élevée.
   1. Réinitialisez la variable `Key Rollover Required` indicateur dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

## Logique de désinscription des domaines {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

L’implémentation de référence applique la logique suivante pour la désinscription de domaine basée sur l’identité :

1. Déterminez le nom de domaine à affecter à cet utilisateur.

   Le nom de domaine est `namequalifier:username`, qui est extrait du jeton d’authentification. Si aucun jeton n’est disponible, renvoie une erreur `DOM_AUTHENTICATION_REQUIRED (503)` survient.
1. Recherchez le nom de domaine demandé dans le `DomainServerInfo` table.
1. Recherchez le nom de domaine dans le `UserDomainMembership` table.
1. Comparez chaque ID d’ordinateur trouvé avec celui de l’ordinateur dans la requête.
1. Localisez l’entrée correspondante dans la variable `UserDomainRefCount` table.

   Si une entrée correspondante n’est pas localisée, renvoie une erreur .

1. S’il ne s’agit pas d’une demande d’aperçu, supprimez l’entrée de la `UserDomainRefCount` table.
1. S’il n’y a pas d’entrées supplémentaires dans cette table pour la machine, supprimez l’entrée de `UserDomainMembership` et définissez la variable [!DNL Key Rollover Required] dans le `DomainServerInfo` .

Chaque utilisateur peut enregistrer un petit nombre de machines afin que vous puissiez utiliser l’identifiant complet de l’ordinateur et le `matches()` pour comptabiliser les machines. Un utilisateur pouvant s’enregistrer plusieurs fois, par le biais de plusieurs applications AIR ou de lecteurs dans différents navigateurs, le serveur doit tenir à jour un nombre de références afin que la désinscription puisse également être comptabilisée.

>[!NOTE]
>
>La désinscription n’est pas terminée tant que tous les jetons de domaine de l’ordinateur ne sont pas rendus.

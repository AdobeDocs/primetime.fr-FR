---
description: 'null'
seo-description: 'null'
seo-title: Logique d'enregistrement des domaines basée sur l'identité
title: Logique d'enregistrement des domaines basée sur l'identité
uuid: bc13f7c2-9a20-4f80-b96f-05f7a0fcc343
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---


# Logique d&#39;enregistrement de domaine basée sur l&#39;identité{#identity-based-domain-registration-logic}

## Logique d&#39;enregistrement de domaine {#section_149C247458954877AF158B4A09A8526B}

L’implémentation de référence applique la logique suivante pour l’enregistrement de domaine basé sur l’identité :

1. Déterminez le nom de domaine à attribuer à un utilisateur désigné.

   Le nom de domaine ( `namequalifier:username`) est extrait du jeton d’authentification. Si un jeton n’est pas disponible, une erreur est générée.
1. Recherchez le nom de domaine dans la table `DomainServerInfo`.

   Si aucune entrée n&#39;est trouvée, insérez une entrée. Les valeurs par défaut sont les suivantes :

   * `authentication required`
   * `max domain membership=5`

   .

1. Pour vérifier que le périphérique a été enregistré avec le domaine :

   1. Recherchez `domainname` dans le tableau `UserDomainMembership` :

      1. Pour chaque ID d’ordinateur qui se trouve, comparez l’ID à celui de l’ordinateur dans la requête.
      1. S&#39;il s&#39;agit d&#39;un nouvel ordinateur, ajoutez une entrée à la table `UserDomainMembership`.
      1. Recherchez les enregistrements correspondants dans la table `UserDomainRefCount`.
      1. Si une entrée n&#39;existe pas pour ce GUID d&#39;ordinateur, ajoutez un enregistrement.
   1. S&#39;il s&#39;agit d&#39;un nouveau périphérique et que la valeur `Max Membership` a été atteinte, l&#39;erreur de retour est renvoyée.


1. Recherchez toutes les clés de domaine pour ce domaine dans la table `DomainKeys` :

   1. Si `DomainServerInfo` indique que les clés doivent être reportées, générez une nouvelle paire de clés,
   1. Enregistrez la paire dans la table `DomainKeys`, avec une version de clé supérieure à la clé existante la plus élevée.
   1. Réinitialisez l&#39;indicateur `Key Rollover Required` dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

## Logique de désenregistrement de domaine {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

L’implémentation de référence applique la logique suivante pour le désenregistrement de domaine basé sur l’identité :

1. Déterminez le nom de domaine à attribuer à cet utilisateur.

   Le nom de domaine est `namequalifier:username`, extrait du jeton d’authentification. Si aucun jeton n’est disponible, l’erreur de renvoi `DOM_AUTHENTICATION_REQUIRED (503)` se produit.
1. Recherchez le nom de domaine demandé dans la table `DomainServerInfo`.
1. Recherchez le nom de domaine dans la table `UserDomainMembership`.
1. Comparez chaque ID d’ordinateur trouvé avec l’ID d’ordinateur dans la requête.
1. Localisez l&#39;entrée correspondante dans la table `UserDomainRefCount`.

   Si une entrée correspondante n’est pas trouvée, renvoie une erreur.

1. S&#39;il ne s&#39;agit pas d&#39;une demande de prévisualisation, supprimez l&#39;entrée de la table `UserDomainRefCount`.
1. S&#39;il n&#39;y a pas d&#39;entrées supplémentaires dans cette table pour l&#39;ordinateur, supprimez l&#39;entrée de `UserDomainMembership` et définissez l&#39;indicateur [!DNL Key Rollover Required] dans la propriété `DomainServerInfo`.

Chaque utilisateur peut enregistrer un petit nombre d&#39;ordinateurs afin que vous puissiez utiliser l&#39;ID d&#39;ordinateur complet et la méthode `matches()` pour comptabiliser les machines. Un utilisateur pouvant s’enregistrer plusieurs fois, par le biais de plusieurs applications AIR ou de lecteurs dans différents navigateurs, le serveur doit conserver un nombre de références afin que la désinscription puisse également être comptabilisée.

>[!NOTE]
>
>La désinscription n&#39;est pas terminée tant que tous les jetons de domaine de l&#39;ordinateur ne sont pas rendus.


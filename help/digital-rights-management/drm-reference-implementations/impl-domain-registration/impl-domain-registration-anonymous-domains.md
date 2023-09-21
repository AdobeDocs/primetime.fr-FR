---
title: Logique de domaine anonyme
description: Logique de domaine anonyme
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Logique de domaine anonyme{#anonymous-domain-logic}

## Logique d’enregistrement des domaines {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

L’implémentation de référence applique la logique suivante pour l’enregistrement de domaine anonyme :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans le `DomainServerInfo` table.
1. Si vous ne parvenez pas à localiser une entrée, insérez-la dans le tableau.

   Les valeurs par défaut sont les suivantes :

   * `authentication is not required`
   * `no membership maximum`

   Si l’authentification est requise pour le domaine demandé, vérifiez qu’un jeton d’authentification valide se trouve dans la requête. Si l’espace de noms Auth est spécifié dans la base de données, le jeton doit correspondre à l’espace de noms Auth spécifié.
1. Si une authentification est requise, mais qu’aucun jeton d’authentification valide n’est disponible, renvoie une erreur. `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Vérifiez si le périphérique est enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans le `DomainMembership` table.
   1. Comparez le GUID de la machine que vous localisez avec le GUID de la machine dans la requête.
   1. S’il s’agit d’une nouvelle machine, ajoutez une entrée dans la variable `DomainMembership` table.
   1. S’il s’agit d’un nouvel appareil et `Max Membership` valeur atteinte, erreur de retour `DOM_LIMIT_REACHED (502)`.

1. Recherchez toutes les clés de domaine pour ce domaine dans le `DomainKeys` table :

   1. If `DomainServerInfo` indique que les clés doivent être roulées et génèrent une nouvelle paire de clés.
   1. Enregistrez la paire de clés dans le `DomainKeys` avec une version de clé supérieure d’un nombre à la clé existante la plus élevée.
   1. Réinitialisez la variable `Key Rollover Required` indicateur dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

## Logique de désinscription des domaines {#section_C968BBFCBFAB4510A903D169F38C9FCE}

L’implémentation de référence applique la logique suivante pour le désenregistrement de domaine anonyme :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans le `DomainServerInfo` table.
1. Si l’authentification est requise pour le domaine demandé, vérifiez qu’un jeton d’authentification valide se trouve dans la requête.

   Le jeton doit également correspondre à l’espace de noms Auth spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID de l’ordinateur dans la variable `DomainMembership` table.

   Si vous ne parvenez pas à localiser une entrée correspondante, renvoyez une erreur. `DEREG_DENIED (401)`.

1. S’il ne s’agit pas d’une demande d’aperçu, supprimez l’entrée de `DomainMembership`et dans `DomainServerInfo`, définissez la variable `Key Rollover Required` Indicateur.

Comme un grand nombre de machines peuvent rejoindre le domaine, vous ne pouvez pas simplement faire correspondre l’identifiant de l’ordinateur. Au lieu de cela, le GUID de machine aléatoire qui est attribué à la machine lors de l’individualisation est appliqué.

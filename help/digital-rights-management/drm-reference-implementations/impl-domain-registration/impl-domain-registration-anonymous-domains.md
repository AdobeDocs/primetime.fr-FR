---
description: 'null'
seo-description: 'null'
seo-title: Logique de domaine anonyme
title: Logique de domaine anonyme
uuid: bd0e8e51-27dc-4ccf-b285-a80c2ab9e260
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Logique de domaine anonyme{#anonymous-domain-logic}

## Logique d&#39;enregistrement de domaine {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

L’implémentation de référence applique la logique suivante pour l’enregistrement de domaine anonyme :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans la `DomainServerInfo` table.
1. Si vous ne parvenez pas à localiser une entrée, insérez-la dans le tableau.

   Les valeurs par défaut sont les suivantes :

   * `authentication is not required`
   * `no membership maximum`
   Si l’authentification est requise pour le domaine demandé, vérifiez qu’un jeton d’authentification valide figure dans la requête. Si l’ Auth  est spécifié dans la base de données, le jeton doit correspondre au Auth  spécifié.
1. Si l’authentification est requise, mais qu’aucun jeton d’authentification valide n’est disponible, renvoie une erreur `DOM_AUTHENTICATION_REQUIRED (503)`.
1. Vérifiez si le périphérique est enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans la `DomainMembership` table.
   1. Comparez le GUID de l’ordinateur que vous localisez avec le GUID de l’ordinateur dans la requête.
   1. S’il s’agit d’une nouvelle machine, ajoutez une entrée dans le `DomainMembership` tableau.
   1. S’il s’agit d’un nouveau périphérique et que `Max Membership` la valeur a été atteinte, l’erreur de renvoi `DOM_LIMIT_REACHED (502)`.

1. Recherchez toutes les clés de domaine de ce domaine dans le `DomainKeys` tableau :

   1. Si `DomainServerInfo` indique que les clés doivent être survolées, générez une nouvelle paire de clés.
   1. Enregistrez la paire de clés dans le `DomainKeys` tableau, avec une version de clé supérieure d’un nombre à la clé existante la plus élevée.
   1. Réinitialisez le `Key Rollover Required` drapeau dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

## Logique de désenregistrement de domaine {#section_C968BBFCBFAB4510A903D169F38C9FCE}

L’implémentation de référence applique la logique suivante pour le désenregistrement de domaine anonyme :

1. Parcourez le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans la `DomainServerInfo` table.
1. Si l’authentification est requise pour le domaine demandé, vérifiez qu’un jeton d’authentification valide figure dans la requête.

   Le jeton doit également correspondre au Auth  qui est spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID de l’ordinateur dans le `DomainMembership` tableau.

   Si vous ne parvenez pas à trouver une entrée correspondante, renvoyez une erreur `DEREG_DENIED (401)`.

1. S’il ne s’agit pas d’une demande de , supprimez l’entrée `DomainMembership`, puis, dans `DomainServerInfo`, définissez l’ `Key Rollover Required` indicateur.

Un grand nombre d’ordinateurs pouvant rejoindre le domaine, vous ne pouvez pas simplement faire correspondre l’ID de l’ordinateur. Au lieu de cela, le GUID de machine aléatoire qui est affecté à la machine pendant l’individualisation est appliqué.

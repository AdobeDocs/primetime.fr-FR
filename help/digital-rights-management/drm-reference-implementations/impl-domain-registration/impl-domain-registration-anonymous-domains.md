---
description: 'null'
seo-description: 'null'
seo-title: Logique de domaine anonyme
title: Logique de domaine anonyme
uuid: bd0e8e51-27dc-4ccf-b285-a80c2ab9e260
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Logique de domaine anonyme {#anonymous-domain-logic}

## Logique d&#39;enregistrement de domaine {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

L’implémentation de référence applique la logique suivante pour l’enregistrement de domaine anonyme :

1. Analyse le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine dans la table `DomainServerInfo`.
1. Si vous ne parvenez pas à trouver une entrée, insérez-la dans le tableau.

   Les valeurs par défaut sont les suivantes :

   * `authentication is not required`
   * `no membership maximum`

   Si une authentification est requise pour le domaine demandé, vérifiez qu’un jeton d’authentification valide figure dans la demande. Si l’Espace de nommage Auth est spécifié dans la base de données, le jeton doit correspondre à l’Espace de nommage Auth spécifié.
1. Si une authentification est requise, mais qu’un jeton d’authentification valide n’est pas disponible, l’erreur de renvoi `DOM_AUTHENTICATION_REQUIRED (503)` est renvoyée.
1. Vérifiez si le périphérique est enregistré auprès du domaine :

   1. Recherchez le nom de domaine dans la table `DomainMembership`.
   1. Comparez le GUID de l&#39;ordinateur que vous localisez avec le GUID de l&#39;ordinateur dans la requête.
   1. S&#39;il s&#39;agit d&#39;un nouvel ordinateur, ajoutez une entrée dans la table `DomainMembership`.
   1. S&#39;il s&#39;agit d&#39;un nouveau périphérique et que la valeur `Max Membership` a été atteinte, l&#39;erreur de renvoi `DOM_LIMIT_REACHED (502)` est renvoyée.

1. Recherchez toutes les clés de domaine pour ce domaine dans la table `DomainKeys` :

   1. Si `DomainServerInfo` indique que les clés doivent être reportées, générez une nouvelle paire de clés.
   1. Enregistrez la paire de clés dans la table `DomainKeys`, avec une version de clé d&#39;un nombre supérieur à la clé existante la plus élevée.
   1. Réinitialisez l&#39;indicateur `Key Rollover Required` dans `DomainServerInfo`.

   1. Pour chaque clé de domaine, générez des informations d’identification de domaine.

## Logique de désenregistrement de domaine {#section_C968BBFCBFAB4510A903D169F38C9FCE}

L’implémentation de référence applique la logique suivante pour le désenregistrement de domaine anonyme :

1. Analyse le nom de domaine à partir de l’URL de demande.
1. Recherchez le nom de domaine demandé dans la table `DomainServerInfo`.
1. Si une authentification est requise pour le domaine demandé, vérifiez qu’un jeton d’authentification valide figure dans la demande.

   Le jeton doit également correspondre à l’Espace de nommage d’authentification spécifié dans la base de données.
1. Recherchez le nom de domaine et le GUID d&#39;ordinateur dans la table `DomainMembership`.

   Si vous ne parvenez pas à trouver une entrée correspondante, renvoyez une erreur `DEREG_DENIED (401)`.

1. S&#39;il ne s&#39;agit pas d&#39;une demande de prévisualisation, supprimez l&#39;entrée de `DomainMembership` et, dans `DomainServerInfo`, définissez l&#39;indicateur `Key Rollover Required`.

Un grand nombre d&#39;ordinateurs pouvant rejoindre le domaine, vous ne pouvez pas simplement faire correspondre l&#39;ID de l&#39;ordinateur. Au lieu de cela, le GUID de machine aléatoire qui est affecté à la machine pendant l&#39;individualisation est appliqué.

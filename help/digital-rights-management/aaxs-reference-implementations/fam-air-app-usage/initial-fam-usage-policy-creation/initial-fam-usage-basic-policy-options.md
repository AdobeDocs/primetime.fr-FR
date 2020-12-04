---
seo-title: Options de stratégie de base
title: Options de stratégie de base
uuid: b09543b6-26a7-4e4d-8e8f-866b4bf9cc50
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# Options de stratégie de base {#basic-policy-options}

Le tableau suivant décrit les préférences de la stratégie de base :

| Préférence | Description |
|---|---|
| Durée de la stratégie | Indique la période de validité du contenu protégé par cette stratégie. |
|  | Début à | Les licences ne peuvent pas être utilisées avant cette date/heure. |
|  | Fin à | Les licences ne peuvent pas être utilisées après cette date/heure. |
|  | Finir après | Indique la durée de validité d’une licence (en minutes), à partir du moment où elle est conditionnée. |
| Mise en cache des licences | Indique si les licences peuvent être mises en cache par le client. |
|  |  | Les licences ne peuvent pas être utilisées après cette date/heure. |
|  | Supprimer après | Indique la durée de validité d’une licence (en minutes), à partir du moment où elle est délivrée par le serveur de licences. |
|  | Cache indéfini | La licence peut être mise en cache indéfiniment sur le client. |
|  | Aucun cache de licence | La licence ne peut pas être mise en cache par le client. Une nouvelle licence doit être obtenue du serveur chaque fois que l’utilisateur lit le contenu. |
| Authentification |  |
|  | Anonyme | Aucune authentification n’est requise pour la vue du contenu. |
|  | Authentifié | L’authentification par nom d’utilisateur/mot de passe est requise. |
| Activer le chaînage de licences | Permet la mise à jour d’une licence à l’aide d’une licence racine parent pour la mise à jour par lots des licences. Une fois la licence feuille expirée, le serveur peut émettre une licence racine au client, qui renouvellera tout le contenu protégé par cette stratégie. |


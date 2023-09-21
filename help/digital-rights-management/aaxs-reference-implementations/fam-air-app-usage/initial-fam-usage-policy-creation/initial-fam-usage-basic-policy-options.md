---
title: Options de stratégie de base
description: Options de stratégie de base
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Options de stratégie de base {#basic-policy-options}

Le tableau suivant décrit les préférences de la stratégie de base :

| Préférence | Description |
|---|---|
| Durée de la stratégie | Indique la période de validité du contenu protégé par cette stratégie. |
|  | Commencer à | Les licences ne peuvent pas être utilisées tant que cette date/heure n’est pas renseignée. |
|  | Fin à | Les licences ne peuvent pas être utilisées après cette date/heure. |
|  | Fin après | Indique la durée de validité d’une licence (en minutes), à partir du moment où elle est conditionnée. |
| Mise en cache des licences | Indique si les licences peuvent être mises en cache par le client. |
|  | | Les licences ne peuvent pas être utilisées après cette date/heure. |
|  | Supprimer après | Indique la durée de validité d’une licence (en minutes), à partir du moment où elle est émise par le serveur de licences. |
|  | Cache indéfini | La licence peut être mise en cache indéfiniment sur le client. |
|  | Aucune mise en cache sous licence | La licence ne peut pas être mise en cache par le client. Une nouvelle licence doit être obtenue du serveur chaque fois que l’utilisateur lit le contenu. |
| Authentification | |
|  | Anonyme | Aucune authentification n’est requise pour afficher le contenu. |
|  | Authentifié | L’authentification par nom d’utilisateur/mot de passe est requise. |
| Activation du chaînage de licences | Permet de mettre à jour une licence à l’aide d’une licence racine parente pour la mise à jour par lots des licences. Une fois la licence feuille expirée, le serveur peut émettre une licence racine au client, qui renouvellera tout le contenu protégé par cette stratégie. |

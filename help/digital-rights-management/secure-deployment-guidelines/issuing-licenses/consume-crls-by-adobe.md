---
description: Le SDK télécharge régulièrement les listes de révocation des certificats publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.
seo-description: Le SDK télécharge régulièrement les listes de révocation des certificats publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.
seo-title: Consommation de listes CRL publiées par Adobe
title: Consommation de listes CRL publiées par Adobe
uuid: 7a9088bd-dde6-4445-958c-3e7272215b3c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Consommation de listes CRL publiées par Adobe{#consuming-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes de révocation des certificats publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.

Le SDK dispose d’une option de configuration permettant d’ignorer les erreurs lors de la récupération des listes de révocation des certificats Adobe et vous ne pouvez appliquer cette option que dans les environnements de développement. Dans les environnements de production, le serveur de licences doit récupérer les listes CRL auprès d’Adobe. Si le serveur de licences ne parvient pas à obtenir une liste de révocation des certificats valide, une erreur s’est produite.

---
description: Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.
title: Consommation de listes CRL publiées par Adobe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# Consommation de listes CRL publiées par Adobe{#consuming-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Vous devez vous assurer que l’accès à ces fichiers n’est pas bloqué ou que l’application de ces listes CRL n’est pas empêchée.

Le SDK dispose d’une option de configuration permettant d’ignorer les erreurs lors de la récupération des listes CRL d’Adobe et vous ne pouvez appliquer cette option que dans les environnements de développement. Dans les environnements de production, le serveur de licences doit récupérer les listes CRL à partir de l’Adobe. Si le serveur de licences ne parvient pas à obtenir une liste de révocation des certificats valide, une erreur s’est produite.

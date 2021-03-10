---
title: Consommer des listes CRL publiées par Adobe
description: Consommer des listes CRL publiées par Adobe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---


# Consommer les listes CRL publiées par Adobe{#consume-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Ne bloquez pas l’accès à ces fichiers ou n’empêchez pas l’application de ces listes CRL.

Le SDK dispose d’une option de configuration permettant d’ignorer les erreurs lors de la récupération des listes CRL d’Adobe. Cette option ne peut être utilisée que dans les environnements de développement. Dans les environnements de production, le serveur de licences doit être en mesure de récupérer les listes CRL à partir de l’Adobe. L&#39;échec d&#39;obtention d&#39;une liste CRL valide est une erreur.

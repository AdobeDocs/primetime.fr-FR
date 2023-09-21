---
title: Utilisation des listes CRL publiées par Adobe
description: Utilisation des listes CRL publiées par Adobe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Utilisation des listes CRL publiées par Adobe{#consume-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Ne bloquez pas l’accès à ces fichiers ou n’empêchez pas l’application de ces listes CRL.

Le SDK dispose d’une option de configuration pour ignorer les erreurs lors de la récupération des listes CRL d’Adobe. Cette option ne peut être utilisée que dans les environnements de développement. Dans les environnements de production, le serveur de licences doit pouvoir récupérer les CRL d’Adobe. L’échec d’obtention d’une liste CRL valide est une erreur.

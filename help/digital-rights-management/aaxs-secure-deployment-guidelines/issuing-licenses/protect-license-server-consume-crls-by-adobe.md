---
seo-title: Consommer des listes CRL publiées par Adobe
title: Consommer des listes CRL publiées par Adobe
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Consommer des listes CRL publiées par Adobe{#consume-crls-published-by-adobe}

Le SDK télécharge régulièrement les listes CRL publiées par Adobe. Ne bloquez pas l’accès à ces fichiers et n’empêchez pas l’application de ces listes CRL.

Le SDK dispose d’une option de configuration permettant d’ignorer les erreurs lors de la récupération des listes CRL Adobe. Cette option ne peut être utilisée que dans les  de développement . Dans le  de production , le serveur de licences doit être en mesure de récupérer les listes CRL d’Adobe. L’échec d’obtention d’une liste CRL valide est une erreur.

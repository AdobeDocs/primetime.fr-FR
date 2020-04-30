---
description: Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.
seo-description: Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.
seo-title: Génération de listes CRL pour compléter celles publiées par Adobe
title: Génération de listes CRL pour compléter celles publiées par Adobe
uuid: 0cc4254d-20a0-4e05-9c5b-0b84a5c833cb
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Génération de listes CRL pour compléter celles publiées par Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.

Le SDK DRM de Primetime vérifie et applique les listes de révocation des certificats Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une liste CRL qui révoque des informations d’identification d’ordinateur supplémentaires en transmettant la liste CRL au SDK DRM de Primetime. Lorsque vous émettez une licence, le SDK vérifie la liste de révocation des certificats d’Adobe et votre liste de révocation des certificats.

Pour générer des listes CRL, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

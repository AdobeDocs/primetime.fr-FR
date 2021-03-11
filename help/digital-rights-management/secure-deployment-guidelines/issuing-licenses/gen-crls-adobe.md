---
description: Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.
title: Génération de listes CRL pour compléter celles publiées par l'Adobe
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Génération de listes CRL pour compléter celles publiées par Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Vous pouvez utiliser Adobe Primetime DRM pour créer des listes CRL qui complètent la liste CRL de l’ordinateur publiée par Adobe.

Le SDK DRM de Primetime vérifie et applique les CRL d’Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une liste CRL qui révoque des informations d’identification d’ordinateur supplémentaires en transmettant la liste CRL au SDK DRM de Primetime. Lorsque vous émettez une licence, le SDK vérifie la liste de révocation des certificats de l’Adobe et la liste de révocation des certificats.

Pour générer des listes CRL, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

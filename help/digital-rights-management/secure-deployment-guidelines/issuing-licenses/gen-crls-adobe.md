---
description: Vous pouvez utiliser Adobe Primetime DRM pour créer des CRL qui complètent la CRL de la machine publiée par Adobe.
title: Génération de listes CRL pour compléter celles publiées par Adobe
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Génération de listes CRL pour compléter celles publiées par Adobe{#generating-crls-to-supplement-those-published-by-adobe}

Vous pouvez utiliser Adobe Primetime DRM pour créer des CRL qui complètent la CRL de la machine publiée par Adobe.

Le SDK DRM Primetime vérifie et applique les listes CRL d’Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une liste de révocation des identifiants de machine supplémentaire en transmettant la liste de révocation des certificats au SDK DRM Primetime. Lorsque vous émettez une licence, le SDK vérifie la CRL d’Adobe et la CRL.

Pour générer des listes CRL, voir [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

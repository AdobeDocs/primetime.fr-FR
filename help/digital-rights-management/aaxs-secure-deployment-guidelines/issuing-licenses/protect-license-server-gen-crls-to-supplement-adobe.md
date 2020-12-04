---
seo-title: Générer des listes CRL pour compléter celles publiées par l'Adobe
title: Générer des listes CRL pour compléter celles publiées par l'Adobe
uuid: 4e93f6d3-5a04-44e9-9e6b-e878798b68f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Générer des listes CRL pour compléter celles publiées par Adobe{#generate-crls-to-supplement-those-published-by-adobe}

Accès à l’Adobe vous permet de créer des listes CRL pour compléter la liste CRL de l’ordinateur publiée par l’Adobe. Le SDK d’accès aux Adobes vérifie et applique les listes CRL d’Adobe, mais vous pouvez interdire d’autres ordinateurs clients en créant une liste CRL qui révoque des informations d’identification d’ordinateur supplémentaires. Pour ce faire, vous devez transmettre la liste CRL au SDK d’accès à l’Adobe, puis, lors de l’émission d’une licence, le SDK vérifie à la fois la liste CRL de l’Adobe et votre propre liste CRL.

Pour en savoir plus sur la génération de listes CRL, voir `RevocationListFactory` dans *Adobe Access API Reference*.

---
seo-title: Générer des listes CRL pour compléter celles publiées par Adobe
title: Générer des listes CRL pour compléter celles publiées par Adobe
uuid: 4e93f6d3-5a04-44e9-9e6b-e878798b68f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Générer des listes CRL pour compléter celles publiées par Adobe{#generate-crls-to-supplement-those-published-by-adobe}

Adobe Access vous permet de créer des listes CRL pour compléter la liste CRL de l’ordinateur publiée par Adobe. Le kit SDK Adobe Access vérifie et applique les listes CRL Adobe ; toutefois, vous pouvez interdire d’autres ordinateurs clients en créant une liste CRL qui révoque des informations d’identification supplémentaires. Pour ce faire, vous devez transmettre la liste CRL au SDK Adobe Access, puis, lors de l’émission d’une licence, le SDK vérifie la liste CRL Adobe et votre propre liste CRL.

Pour en savoir plus sur la génération de listes CRL, voir `RevocationListFactory` Adobe Access API Reference **(en anglais).

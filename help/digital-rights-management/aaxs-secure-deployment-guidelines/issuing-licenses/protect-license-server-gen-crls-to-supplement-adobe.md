---
title: Générer des listes CRL pour compléter celles publiées par Adobe
description: Générer des listes CRL pour compléter celles publiées par Adobe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Générer des listes CRL pour compléter celles publiées par Adobe{#generate-crls-to-supplement-those-published-by-adobe}

Adobe Access vous permet de créer des listes CRL pour compléter la liste CRL de la machine publiée par Adobe. Adobe Access SDK vérifie et applique les CRL d’Adobe. Cependant, vous pouvez interdire d’autres ordinateurs clients en créant une CRL qui révoque des informations d’identification de machine supplémentaires. Pour ce faire, vous devez transmettre la CRL au SDK d’accès aux Adobes, puis, lors de l’octroi d’une licence, le SDK vérifie à la fois la CRL d’Adobe et votre propre CRL.

Pour en savoir plus sur la génération de listes CRL, voir `RevocationListFactory` in *Référence de l’API Adobe Access*.

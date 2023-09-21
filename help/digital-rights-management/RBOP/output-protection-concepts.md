---
description: Cette section présente un aperçu conceptuel de la configuration, des options et des significations associées à la protection de sortie.
title: Concepts de la RBOP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Concepts de la RBOP {#rbop-concepts}

Cette section présente un aperçu conceptuel de la configuration, des options et des significations associées à la protection de sortie.

Vous définissez vos exigences de protection de sortie en fonction de la résolution dans une structure JSON hiérarchique. *Les exigences de sortie sont basées sur les pixels.*

Au niveau le plus élevé de la spécification JSON, vous pouvez définir la résolution maximale des pixels et les contraintes de pixels pour les résolutions spécifiées :

* `maxPixel` - La résolution maximale des pixels définit la résolution maximale pour laquelle le décryptage aura lieu.
* `pixelConstraints` - Les contraintes de pixel définissent les exigences de sortie qui doivent être appliquées pour une résolution spécifiée.

Vous associez des exigences de sortie à des contraintes de pixel spécifiques. Les types d’exigences que vous pouvez associer à une contrainte de pixel donnée incluent des restrictions pour les connexions numériques, analogiques et hors ligne (OTA).

**Sortie numérique**

L’exigence de sortie numérique peut spécifier des options restrictives, telles que &quot;la protection de sortie numérique est requise&quot; ou &quot;la lecture n’est pas autorisée&quot;. Les exigences de sortie peuvent également spécifier des options moins restrictives telles que &quot;aucune protection ne doit être appliquée&quot; ou &quot;une protection numérique doit être utilisée si elle est disponible&quot;.

**Sortie Analog**

Les connexions de sortie analogique sont plus simples que la sortie numérique ; elles se composent d’une exigence de sortie unique.

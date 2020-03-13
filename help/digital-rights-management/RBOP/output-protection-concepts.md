---
description: Cette section présente un aperçu conceptuel de la configuration, des options et des significations associées à la protection de la sortie.
seo-description: Cette section présente un aperçu conceptuel de la configuration, des options et des significations associées à la protection de la sortie.
seo-title: Concepts RBOP
title: Concepts RBOP
uuid: fc19c3c9-39a1-4b62-b763-101e5454a01f
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Concepts RBOP {#rbop-concepts}

Cette section présente un aperçu conceptuel de la configuration, des options et des significations associées à la protection de la sortie.

Vous définissez vos exigences de protection de sortie basée sur la résolution dans une structure JSON hiérarchique. *Les exigences de sortie sont basées sur les pixels.*

Au niveau le plus élevé de la spécification JSON, vous pouvez définir la résolution maximale en pixels et les contraintes en pixels pour les résolutions spécifiées :

* `maxPixel` - La résolution maximale en pixels définit la résolution maximale pour laquelle le déchiffrement aura lieu.
* `pixelConstraints` - Les contraintes de pixels définissent les exigences de sortie qui doivent être appliquées pour une résolution spécifiée.

Vous associez les exigences de sortie à des contraintes de pixels spécifiques. Les types d’exigences que vous pouvez associer à une contrainte de pixels donnée incluent des restrictions pour les connexions numériques, analogiques et en direct (OTA).

**Sortie numérique**

Les exigences de sortie numérique peuvent spécifier des options restrictives, telles que &quot;la protection de sortie numérique est requise&quot; ou &quot;la lecture n’est pas autorisée&quot;. Les exigences de sortie peuvent également spécifier des options moins restrictives, telles que &quot;aucune protection ne doit être appliquée&quot; ou &quot;une protection numérique doit être utilisée si elle est disponible&quot;.

**Sortie analogique**

Les connexions de sortie analogique sont plus simples que la sortie numérique ; elles consistent en une seule exigence de sortie.

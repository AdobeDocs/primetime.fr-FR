---
title: Niveau de chiffrement partiel
description: Niveau de chiffrement partiel
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Niveau de chiffrement partiel {#partial-encryption-level}

Cette option de conditionnement spécifie si toutes les images, ou seulement un sous-ensemble d’images, doivent être chiffrées. Il existe trois niveaux de cryptage : bas, moyen et élevé.

>[!NOTE]
>
>Le chiffrement partiel s’applique uniquement au suivi vidéo dans les fichiers F4V/MP4.

Le cryptage partiel est conçu pour fournir une granularité aux fournisseurs de contenu afin de coder le contenu en plusieurs parties. Le cryptage du contenu ajoute la surcharge du processeur à l’appareil qui décrypte et affiche le contenu. Utilisez un cryptage partiel pour réduire la surcharge du processeur tout en conservant une protection très forte du contenu. L’utilisation de cette fonctionnalité est un cas de figure motivant : une seule partie de contenu est destinée à être lisible sur les périphériques à faible, moyen et élevé.

En raison de la nature du codage vidéo, il n’est pas nécessaire de chiffrer 100 % de la vidéo pour rendre la vidéo non lisible si elle est volée. Le cryptage partiel comporte trois paramètres, faible, moyen et élevé, et les pourcentages de cryptage associés dépendent du mode de codage de la vidéo. En raison de cette dépendance de codage, le pourcentage de votre contenu chiffré se situe dans les plages suivantes :

* Élevé : crypte tous les exemples.
* Moyen : crypte une cible à 50 % des données.
* Faible : crypte une cible de 20 à 30 % des données.

Ces paramètres ont été conçus selon la règle suivante : tout contenu chiffré en basse résolution est également chiffré en moyenne. Cela permet de s’assurer que le même élément de contenu distribué à faible chiffrement par une partie et distribué à moyen chiffrement par une autre partie ne compromet pas la protection du contenu.

Exemple de cas d’utilisation : la réduction du niveau de chiffrement réduit la surcharge de décryptage sur le client et améliore les performances de lecture sur les ordinateurs bas de gamme.

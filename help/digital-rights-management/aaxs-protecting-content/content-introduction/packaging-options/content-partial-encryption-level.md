---
seo-title: Niveau de chiffrement partiel
title: Niveau de chiffrement partiel
uuid: 462ca2d0-0d37-43a8-b8a0-8a25ecf73ce1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# Niveau de chiffrement partiel{#partial-encryption-level}

Indique si toutes les images, ou seulement un sous-ensemble de cadres, doivent être chiffrées. Il existe trois niveaux de chiffrement : bas, moyen et élevé.

>[!NOTE]
>
>Pour le suivi vidéo dans les fichiers F4V/H.264 uniquement.

Le chiffrement partiel est conçu pour fournir une granularité aux fournisseurs de contenu afin de coder le contenu en parties. Le chiffrement du contenu ajoute une surcharge CPU au périphérique qui décrypte et affiche le contenu. Utilisez le cryptage partiel pour réduire la charge du processeur tout en maintenant une protection très forte du contenu. L’utilisation de cette fonctionnalité présente un intérêt particulier : il s’agit d’un seul élément de contenu destiné à être lisible sur les périphériques à faible, moyen et haut débit.

En raison de la nature de l’encodage vidéo, il n’est pas nécessaire de chiffrer 100 % de la vidéo pour la rendre illisible en cas de vol. Le chiffrement partiel a trois paramètres, faible, moyen et élevé, et les pourcentages de chiffrement associés dépendent du mode de codage de la vidéo. En raison de cette dépendance de codage, le pourcentage de votre contenu chiffré se situe dans les plages suivantes :

* Élevée : Chiffre tous les échantillons.
* Moyen : Chiffre une cible contenant 50 % des données.
* Faible : Chiffre une cible de 20 à 30 % des données.

Ces paramètres ont été conçus avec la règle suivante : Tout contenu chiffré à faible valeur est également chiffré à moyenne valeur. Cela garantit que le même élément de contenu distribué à faible chiffrement par une partie et distribué à moyen chiffrement par une autre partie ne compromet pas la protection du contenu.

Exemple de cas d’utilisation : La réduction du niveau de chiffrement réduit les frais de déchiffrement sur le client et améliore les performances de lecture sur les ordinateurs bas de gamme.

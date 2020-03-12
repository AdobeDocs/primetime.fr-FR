---
seo-title: Niveau de chiffrement partiel
title: Niveau de chiffrement partiel
uuid: dbd9ce92-c829-4cad-9ac4-c57bd4f70345
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Niveau de chiffrement partiel {#partial-encryption-level}

Cette option d’assemblage spécifie si toutes les images, ou seulement un sous-ensemble de cadres, doivent être chiffrées. Il existe trois niveaux de chiffrement : low, medium et high.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Le chiffrement partiel s’applique à la piste vidéo dans les fichiers F4V/MP4 uniquement.

Le chiffrement partiel est conçu pour donner aux fournisseurs de contenu la granularité nécessaire pour coder le contenu en parties. Le chiffrement du contenu ajoute une surcharge CPU au périphérique qui décrypte et affiche le contenu. Utilisez le chiffrement partiel pour réduire la charge du processeur tout en maintenant une protection très forte du contenu. L’utilisation de cette fonctionnalité est motivante car elle s’accompagne d’un seul élément de contenu destiné à être lisible sur les périphériques à faible, moyen et élevé.

En raison de la nature du codage vidéo, il n’est pas nécessaire de chiffrer 100 % de la vidéo pour la rendre illisible en cas de vol. Le chiffrement partiel a trois paramètres : faible, moyen et élevé. Les pourcentages de chiffrement associés dépendent du mode de codage de la vidéo. En raison de cette dépendance au codage, le pourcentage de votre contenu chiffré se situe dans les plages suivantes :

* Élevée : Chiffre tous les échantillons.
* Moyen : Chiffre un  50 % des données.
* Faible : Chiffre un  20 à 30 % des données.

Ces paramètres ont été conçus à l’aide de la règle suivante : Tout contenu chiffré à un niveau inférieur est également chiffré à un niveau moyen. Cela garantit que le même élément de contenu distribué à faible chiffrement par une partie et distribué à moyen chiffrement par une autre partie ne compromet pas la protection du contenu.

Exemple de cas d’utilisation : La réduction du niveau de chiffrement réduit les frais de déchiffrement sur le client et améliore les performances de lecture sur les ordinateurs bas de gamme.

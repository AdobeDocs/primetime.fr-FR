---
description: Adobe Primetime DRM est un Digital Rights Management avancé (DRM) et une solution de protection du contenu pour le contenu audiovisuel de grande valeur. Dans les applications qui prennent en charge la création d’API Java, vous pouvez utiliser le SDK DRM Primetime pour spécifier les stratégies DRM, appliquer ces stratégies au contenu et chiffrer ce contenu.
title: Nouveautés d’Adobe Primetime DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Nouveautés d’Adobe Primetime DRM{#what-is-new-in-adobe-primetime-drm}

Adobe Primetime DRM est un Digital Rights Management avancé (DRM) et une solution de protection du contenu pour le contenu audiovisuel de grande valeur. Dans les applications qui prennent en charge la création d’API Java, vous pouvez utiliser le SDK DRM Primetime pour spécifier les stratégies DRM, appliquer ces stratégies au contenu et chiffrer ce contenu.

>[!NOTE]
>
>Primetime DRM s’appelait auparavant Accès aux Adobes, et avant cela, Flash Access.

Voici une présentation générale du processus de protection du contenu :

1. Utilisez les API Java DRM pour définir les propriétés de stratégie DRM et les paramètres de chiffrement.
1. Créez une stratégie DRM qui décrit les rôles d’utilisation de tout contenu.

   Vous pouvez créer un nombre illimité de stratégies DRM. La plupart des utilisateurs créent un petit nombre de stratégies, puis les appliquent à de nombreux fichiers.
1. Regroupez un fichier multimédia.

   *`Packaging a file`* signifie que vous chiffrez le fichier, puis appliquez une stratégie DRM au fichier.
1. Mettez en oeuvre le serveur de licences pour émettre une licence à l’utilisateur.

Une fois ces étapes terminées, votre contenu chiffré est prêt pour le déploiement. Après le déploiement, un client peut demander une licence au serveur de licences et, à réception, peut lire le contenu.

Le SDK DRM Primetime fournit une API Java pour effectuer ces tâches. Le SDK comprend des mises en oeuvre de référence du serveur de licences et des outils de ligne de commande, qui sont tous deux basés sur les API Java du SDK DRM.

Les fonctionnalités décrites ci-dessous sont nouvelles dans cette version.

## Nouvelles fonctionnalités {#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **Hard Stop -** Vous pouvez indiquer si la lecture s’arrête ou se poursuit à la fin d’une fenêtre de lecture.
* **Contrôle de sortie dépendant de la résolution -** Vous pouvez spécifier des contraintes de sortie en fonction de la résolution des pixels.
* **Anonymisation des réponses du serveur de licences -** Pour améliorer la confidentialité avec les protocoles de serveur de licences DRM Primetime, le numéro de série du certificat de transport sera réduit à zéro pour les réponses du serveur de licences aux clients pris en charge.

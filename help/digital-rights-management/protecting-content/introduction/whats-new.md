---
description: Adobe Primetime DRM est une solution de protection de contenu et de Digital Rights Management avancée pour les contenus audiovisuels de grande valeur. Dans les applications qui prennent en charge la création d’API Java, vous pouvez utiliser le SDK DRM Primetime pour spécifier des stratégies DRM, appliquer ces stratégies au contenu et chiffrer ce contenu.
seo-description: Adobe Primetime DRM est une solution de protection de contenu et de Digital Rights Management avancée pour les contenus audiovisuels de grande valeur. Dans les applications qui prennent en charge la création d’API Java, vous pouvez utiliser le SDK DRM Primetime pour spécifier des stratégies DRM, appliquer ces stratégies au contenu et chiffrer ce contenu.
seo-title: Nouveautés de la DRM en Adobe Primetime
title: Nouveautés de la DRM en Adobe Primetime
uuid: 3c8da594-a231-4496-bffc-130775ecae50
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Nouveautés de l’Adobe Primetime DRM{#what-is-new-in-adobe-primetime-drm}

Adobe Primetime DRM est une solution de protection de contenu et de Digital Rights Management avancée pour les contenus audiovisuels de grande valeur. Dans les applications qui prennent en charge la création d’API Java, vous pouvez utiliser le SDK DRM Primetime pour spécifier des stratégies DRM, appliquer ces stratégies au contenu et chiffrer ce contenu.

>[!NOTE]
>
>Primetime DRM s&#39;appelait auparavant Adobe Access, et avant cela, Flash Access.

Voici une présentation détaillée du processus de protection du contenu :

1. Utilisez les API Java DRM pour définir les propriétés de la stratégie DRM et les paramètres de chiffrement.
1. Créez une stratégie DRM décrivant les rôles d’utilisation de tout contenu.

   Vous pouvez créer n’importe quel nombre de stratégies DRM. La plupart des utilisateurs créent un petit nombre de stratégies, puis les appliquent à de nombreux fichiers.
1. Assemblage d’un fichier multimédia.

   *`Packaging a file`* signifie que vous chiffrez le fichier, puis appliquez une stratégie DRM au fichier.
1. Mettez en oeuvre le serveur de licences pour délivrer une licence à l’utilisateur.

Une fois ces étapes terminées, votre contenu chiffré est prêt pour le déploiement. Après le déploiement, un client peut demander une licence au serveur de licences et, à réception, peut lire le contenu.

Le SDK DRM de Primetime fournit une API Java pour compléter ces tâches. Le SDK comprend des implémentations de référence du serveur de licences et des outils de ligne de commande, qui sont tous deux basés sur les API Java du SDK DRM.

Les fonctionnalités décrites ci-dessous sont nouvelles dans cette version.

## Nouvelles fonctionnalités {#section_F6BA874CEAE24610920BC3A4C6D20EBA}

* **Arrêt définitif :** vous pouvez indiquer si la lecture s’arrête ou continue à la fin d’une fenêtre de lecture.
* **Commandes de sortie dépendantes de la résolution :** vous pouvez spécifier des contraintes de sortie basées sur des résolutions de pixels.
* **Anonymisation des réponses du serveur de licences :** pour améliorer la confidentialité des protocoles du serveur de licences DRM Primetime, le numéro de série du certificat de transport sera réduit à zéro pour les réponses du serveur de licences aux clients pris en charge.


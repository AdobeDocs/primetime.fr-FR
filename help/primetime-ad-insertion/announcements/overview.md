---
title: Annonces des Ad Insertion Adobe Primetime
description: Annonces à propos des dernières mises à jour de fonctionnalités et autres informations connexes sur l’Ad Insertion Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Annonces Ad Insertion Primetime

## Réduction des erreurs de publicité programmée via les dépassements de délai de résolution de publicité

Publié le 1er décembre 2020

Adobe vise à aider nos clients Ad Insertion Primetime à maximiser la monétisation de leur inventaire publicitaire. Nous accordons une attention particulière à la réduction des complexités de la satisfaction de la demande programmatique, qui représente plus des trois quarts des dépenses de publicité vidéo numérique américaines selon eMarketer. La vente par programmation permet aux éditeurs de maximiser la demande pour leur inventaire publicitaire, ce qui entraîne des taux de remplissage et des rendements plus élevés. Mais il augmente également l’exposition aux erreurs publicitaires telles que les réponses VAST incorrectes, les erreurs HTTP et autres qui peuvent entraîner une perte de recettes et/ou de mauvaises expériences de visionneuse.

Un problème courant est la lenteur des réponses publicitaires de la part des partenaires programmatiques. En règle générale, les transactions publicitaires programmatiques se produisent en millisecondes. Cependant, il arrive qu’une source de demande unique prenne un temps excessif pour y répondre. Un délai d’un seul fournisseur peut avoir un impact sur l’ensemble du processus d’exécution de la publicité, ce qui entraîne des écrans vierges temporaires pour la visionneuse, des emplacements de publicité vides ou, dans les cas extrêmes, la nécessité de redémarrer un flux vidéo. Malheureusement, identifier et contourner les sources de demande lente est un défi majeur.

Pour résoudre ce problème, Adobe a ajouté de nouveaux outils à l’Ad Insertion Primetime qui permettent aux clients de définir des contraintes de temps pour la résolution des publicités. Si vous définissez ces règles, les sources de demande lentes sont automatiquement contournées, ce qui permet aux lecteurs vidéo d’obtenir des réponses publicitaires en temps voulu. Cela permet aux éditeurs de limiter considérablement les interruptions provenant de sources de demande lentes, ce qui les aide à maximiser les taux de remplissage d’inventaire et à offrir des expériences de visionnage ininterrompues et de qualité télévisuelle.

Pour activer le délai d’expiration de la résolution des publicités dans l’Ad Insertion Primetime, modifiez vos API de bootstrap afin d’inclure le paramètre ptadtimeout (durée en millisecondes).  Les requêtes de publicité qui ne se terminent pas avant le délai d’expiration ne sont pas regroupées (les publicités de secours sont traitées).

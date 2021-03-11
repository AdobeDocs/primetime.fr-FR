---
title: Annonces Ad Insertion
description: Annonces de nouvelles fonctionnalités récentes et autres informations connexes sur l’Ad Insertion Primetime
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Annonces Ad Insertion Primetime

## Réduction des erreurs de publicité par le biais des dépassements de délai de résolution des publicités

Publié le 1er décembre 2000

L&#39;Adobe vise à aider nos clients Ad Insertion Primetime à optimiser la monétisation de leur stock publicitaire. Nous accordons une attention particulière à la réduction des complexités de la réalisation de la demande programmatique, qui représente plus des trois quarts des dépenses de vidéo numérique américaines selon eMarketer. La vente par programmation permet aux éditeurs de maximiser la demande pour leur stock publicitaire, ce qui entraîne des taux de remplissage et des rendements plus élevés. Mais il augmente également l’exposition aux erreurs publicitaires, telles que les réponses VAST mal formées, les erreurs HTTP et autres, qui peuvent entraîner des pertes de recettes et/ou de mauvaises expériences de visionneuse.

L&#39;un des problèmes courants est la lenteur des interventions des partenaires programmatiques. En règle générale, les transactions publicitaires programmatiques se produisent en millisecondes. Cependant, il arrive parfois qu&#39;une seule source de demande prenne un temps excessif pour répondre. Un délai d’un fournisseur unique peut avoir un impact sur l’ensemble du processus d’exécution des publicités, ce qui entraîne des écrans vierges temporaires pour la visionneuse, des créneaux publicitaires vides ou, dans certains cas extrêmes, la nécessité de redémarrer un flux vidéo. Malheureusement, l&#39;identification et le contournement des sources de demande lentes constituent un défi majeur.

Pour résoudre ce problème, l’Adobe a ajouté de nouveaux outils à l’Ad Insertion Primetime qui permettent aux clients de définir des contraintes de temps pour la résolution des publicités. Si vous définissez ces règles, les sources de demande lentes sont automatiquement ignorées, ce qui permet aux lecteurs vidéo d’obtenir des réponses publicitaires en temps opportun. Cela permet aux éditeurs de limiter considérablement les interruptions dues à la lenteur des sources de demande, ce qui les aide à optimiser les taux de remplissage des stocks et à offrir des expériences de visualisation ininterrompues et de qualité télévisuelle.

Pour activer le délai d’expiration de la résolution des publicités dans l’Ad Insertion Primetime, modifiez vos API d’amorçage afin d’inclure le paramètre ptadtimeout (durée en millisecondes).  Les requêtes publicitaires qui ne se terminent pas avant la durée du délai d’expiration ne seront pas assemblées (les annonces de secours seront traitées).
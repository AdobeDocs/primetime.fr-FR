---
description: L’implémentation de référence illustre comment configurer le lecteur pour les publicités, ce qui inclut la configuration des métadonnées vidéo pour l’insertion de publicités et la résolution des publicités preroll, mid, mid et post-roll dans des flux vidéo VOD ou des flux vidéo linéaire/en direct. Il illustre également comment gérer les publicités cliquables.
title: Insertion publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Insertion d&#39;annonce {#ad-insertion}

L’implémentation de référence illustre comment configurer le lecteur pour les publicités, ce qui inclut la configuration des métadonnées vidéo pour l’insertion de publicités et la résolution des publicités preroll, mid, mid et post-roll dans des flux vidéo VOD ou des flux vidéo linéaire/en direct. Il illustre également comment gérer les publicités cliquables.

Le processus de configuration d’un lecteur pour l’insertion d’annonces publicitaires comprend :

* **Flux d’entrée :** remplissage d’un flux d’entrée avec des métadonnées publicitaires. Voir [Format de catalogue](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Adaptateur de flux de mise en oeuvre de référence :** analyse du flux d’entrée pour renseigner un objet de métadonnées publicitaires.
* **AdsManager:** Utilisation d’AdsManager pour récupérer les métadonnées publicitaires et créer le AdProvider correspondant.
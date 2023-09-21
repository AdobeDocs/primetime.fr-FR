---
description: La mise en oeuvre de référence illustre la configuration du lecteur pour les publicités, ce qui inclut la configuration des métadonnées vidéo pour l’insertion de publicités et la résolution des publicités preroll, mid et post-roll dans des flux vidéo VOD ou vidéo linéaire. Il illustre également la gestion des publicités cliquables.
title: Insertion de publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Insertion de publicités {#ad-insertion}

La mise en oeuvre de référence illustre la configuration du lecteur pour les publicités, ce qui inclut la configuration des métadonnées vidéo pour l’insertion de publicités et la résolution des publicités preroll, mid et post-roll dans des flux vidéo VOD ou vidéo linéaire. Il illustre également la gestion des publicités cliquables.

Le processus de configuration d’un lecteur pour l’insertion de publicités comprend :

* **Flux d’entrée :** Renseignement d’un flux d’entrée avec des métadonnées publicitaires. Voir [Format du catalogue](../set-up-dev-environment/exploring-code/catalog-format.md).
* **Adaptateur de flux de mise en oeuvre de référence :** Analyse du flux d’entrée pour remplir un objet de métadonnées de publicité.
* **AdsManager :** Utilisation d’AdsManager pour récupérer les métadonnées publicitaires et créer le AdProvider correspondant.

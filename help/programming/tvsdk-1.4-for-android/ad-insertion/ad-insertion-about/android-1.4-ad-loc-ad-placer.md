---
description: Il existe plusieurs façons de déterminer l’insertion et l’emplacement des publicités.
seo-description: Il existe plusieurs façons de déterminer l’insertion et l’emplacement des publicités.
seo-title: Insertion et placement de publicités
title: Insertion et placement de publicités
uuid: 1d4d6364-1c49-402b-9b72-8c185b1c94e1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Insertion et placement de publicités{#ad-insertion-and-placement}

Il existe plusieurs façons de déterminer l’insertion et l’emplacement des publicités.

## Insertion d’une publicité {#section_1F7581B987704E318E064082190E8243}

Voici un aperçu du processus utilisé pour déterminer l’insertion d’annonces :

1. **Détection** des opportunités : Le SDK TVSDK utilise les informations du flux pour détecter les emplacements possibles et désirés pour les publicités.
1. **Résolution** de la publicité : Le TVSDK communique avec un serveur de publication pour récupérer les publicités à diviser en contenu.
1. **Emplacement** de la publicité : Le SDK TVSDK charge les publicités spécifiées et les place dans des pauses publicitaires sur la chronologie du contenu aux emplacements spécifiés et recalcule la chronologie virtuelle, si nécessaire.

## Emplacement de la publicité {#section_B9D63F7409A2447F9FF209289BE5D3D5}

Le SDK TVSDK peut obtenir des emplacements pour un emplacement publicitaire possible à partir des sources suivantes :

* **Métadonnées/indices de manifeste**

   Le TVSDK détecte les indices, extrait les informations nécessaires de ces indices et communique avec un serveur de publicité pour obtenir les annonces correspondantes. Cette source est commune aux flux en direct/linéaires.

   Le kit TVSDK remplace généralement le contenu principal par les publicités à l’emplacement indiqué par les métadonnées/repères ; dans le cas contraire, le client abandonnerait de plus en plus son point de vie réel.

* **Le mappage du serveur de publicité**

   En règle générale, les métadonnées de ces flux sont enregistrées dans le serveur de publicité avant la lecture. Le SDK TVSDK récupère la chronologie des publicités et les publicités correspondantes du serveur. Cette source est courante pour les flux VOD.

   Le kit TVSDK insère généralement les publicités résolues dans le contenu principal, comme indiqué par le mappage du serveur.

>[!NOTE]
>
>Par défaut, TVSDK utilise des indices manifestes pour les flux en direct/linéaires et des cartes de serveur de publicité pour les flux VOD. Toutefois, pour prendre en charge la relecture de  complète pour les  de en direct, votre application doit prendre des mesures supplémentaires.


---
description: Il existe plusieurs façons de déterminer l’insertion et le placement de publicités.
title: Insertion et emplacement des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Insertion et emplacement des publicités{#ad-insertion-and-placement}

Il existe plusieurs façons de déterminer l’insertion et le placement de publicités.

## Insertion de publicités {#section_1F7581B987704E318E064082190E8243}

Voici un aperçu du processus utilisé pour déterminer l’insertion de publicités :

1. **Détection des opportunités**: TVSDK utilise les informations de diffusion pour détecter les emplacements possibles et souhaités pour les publicités.
1. **Résolution des publicités**: TVSDK communique avec un serveur de publicité pour récupérer les publicités à scinder dans le contenu.
1. **Emplacement des publicités**: TVSDK charge les publicités spécifiées et les place dans les coupures publicitaires sur la chronologie du contenu aux emplacements spécifiés et recalcule la chronologie virtuelle, si nécessaire.

## Emplacement des publicités {#section_B9D63F7409A2447F9FF209289BE5D3D5}

TVSDK peut obtenir des emplacements pour un emplacement publicitaire possible à partir des sources suivantes :

* **Métadonnées/repères de manifeste**

  TVSDK détecte les indices, extrait les informations nécessaires de ces indices et communique avec un serveur de publicité pour obtenir les publicités correspondantes. Cette source est courante pour les flux en direct/linéaires.

  Le TVSDK remplace généralement le contenu principal par les publicités à l’emplacement indiqué par les métadonnées/signaux ; dans le cas contraire, le client abandonnerait de plus en plus de temps le point d’entrée réel.

* **Carte du serveur de publicité**

  En règle générale, les métadonnées relatives à ces flux sont enregistrées dans le serveur de publicité avant la lecture. TVSDK récupère la chronologie de la publicité et les publicités correspondantes à partir du serveur. Cette source est courante pour les flux VOD.

  TVSDK insère généralement les publicités résolues dans le contenu principal, comme indiqué par le mappage du serveur.

>[!NOTE]
>
>Par défaut, TVSDK utilise des signaux manifestes pour les diffusions en direct/linéaires et les mappages de serveur de publicité pour les diffusions VOD. Toutefois, pour prendre en charge la relecture d’événement complet pour les événements en direct, votre application doit prendre des mesures supplémentaires.

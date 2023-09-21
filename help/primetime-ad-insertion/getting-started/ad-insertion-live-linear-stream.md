---
title: Utilisation d’un Ad Insertion dans un flux continu en direct/linéaire
description: Utilisation de l’Ad Insertion dans un flux en direct/linéaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Utilisation d’un Ad Insertion dans un flux continu en direct/linéaire {#ad-insertion-live-linear-stream}

L’Ad Insertion Primetime permet aux éditeurs de gérer des situations standard et complexes d’insertion de publicités qui se produisent pendant les flux en direct/linéaires.

## Formats de repère pris en charge {#cue-formats-supported}

Primetime Ad Insertion prend en charge un large éventail de formats de repère standard et non standard, notamment :

* DPI SCTE-35 (marqueurs d’annonce améliorés SCTE-35)

* [Spécification de signal pour l’insertion de programmes numériques Adobe](assets/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* SCTE-35 binaire (HLS et DASH)

* Texte SCTE-35 (HLS et DASH)

Contactez votre représentant de l’assistance pour Primetime pour plus de détails ou pour tout autre format de repère pris en charge.

## Prise en charge partielle des coupures publicitaires {#partial-ad-break-support}

Les coupures publicitaires partielles peuvent être utilisées lorsqu’une visionneuse entre dans un flux linéaire/en direct après le démarrage d’une coupure publicitaire.  Par exemple, si une visionneuse entre dans une coupure publicitaire longue de 2 h 00 à 1 h 00, l’insertion de coupure publicitaire partielle garantit que les publicités seront diffusées pendant le temps restant. Sans insertion de coupure publicitaire partielle, aucune publicité ne serait diffusée à cette visionneuse pendant la coupure. L’Ad Insertion Primetime active par défaut l’insertion de coupures publicitaires partielles si les balises appropriées sont présentes dans le ou les flux multimédia.

## Retour anticipé (sortie anticipée de la publicité) {#early-return-early-ad-exit}

Il peut être nécessaire de revenir tôt d’une coupure publicitaire dans un flux linéaire/en direct, par exemple lorsqu’un événement sportif revient soudainement à l’action. Chaque format de prise de décision relative aux publicités contient une balise &quot;indice&quot; (publicités) ou &quot;indice&quot; (contenu).  Si une balise &quot;indice&quot; est rencontrée avant la fin d’une coupure publicitaire, l’Ad Insertion Adobe Primetime honore le repère.  Contactez votre module de contenu pour activer un retour anticipé.

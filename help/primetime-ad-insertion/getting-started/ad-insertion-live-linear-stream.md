---
title: Utiliser l’Ad Insertion dans le flux en direct/linéaire
description: Utilisation d’un Ad Insertion dans un flux en direct/linéaire
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# Utiliser l’Ad Insertion dans le flux en direct/linéaire {#ad-insertion-live-linear-stream}

L’Ad Insertion Primetime permet aux éditeurs de gérer les situations standard et complexes d’insertion de publicités survenant pendant les flux en direct/linéaires.

## Formats de codes pris en charge {#cue-formats-supported}

L&#39;Ad Insertion Primetime prend en charge un large éventail de formats standard et non standard de signaux, notamment :

* PPP SCTE-35 (marques d’annonce améliorées SCTE-35)

* [Spécification de signalisation pour l&#39;insertion de Programmes numériques d&#39;Adobe](https://www.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* SCTE-35 binaire (HLS et DASH)

* Textuel SCTE-35 (HLS et DASH)

Contactez votre représentant du support technique de Primetime pour obtenir des détails supplémentaires ou d&#39;autres formats de indices pris en charge.

## Prise en charge des coupures publicitaires partielles {#partial-ad-break-support}

Des coupures publicitaires partielles peuvent être utilisées lorsqu’une visionneuse entre dans un flux continu linéaire/en direct après le démarrage d’une coupure publicitaire.  Par exemple, si un lecteur entre une coupure publicitaire longue de 2 h 00 à 1 h 00, l’insertion partielle de coupures publicitaires garantit que les publicités seront diffusées pendant la durée restante. Sans insertion partielle de coupures publicitaires, aucune publicité n’est diffusée à cette visionneuse pendant la coupure. Par défaut, l’Ad Insertion Primetime active l’insertion de coupures publicitaires partielles si les balises appropriées sont présentes dans le(s) flux média.

## Retour anticipé (sortie anticipée de l’annonce) {#early-return-early-ad-exit}

Dans certains cas, il peut s’avérer nécessaire de revenir tôt d’une coupure publicitaire dans un flux direct/linéaire, par exemple lorsqu’un événement sportif revient soudainement à l’action. Chaque format de prise de décision d’une publicité contient une balise indiquant &quot;indice&quot; (publicités) ou &quot;indice&quot; (contenu).  Si une balise de connexion est rencontrée avant la fin d’une coupure publicitaire, l’Ad Insertion Adobe Primetime tiendra compte de la notification.  Veuillez contacter votre gestionnaire de contenu pour activer un retour anticipé.
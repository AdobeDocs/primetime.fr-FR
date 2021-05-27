---
title: Notes de mise à jour de PTAI 21.5.1
description: Les notes de mise à jour de l’API décrivent les nouveautés ou les modifications, les problèmes résolus et connus de l’Ad Insertion Primetime en 2021.
exl-id: 39a05f6d-431a-4416-81b1-21d82c0dbd69
source-git-commit: 02e43df4d9b58b4b1ed8fdbc086771bbf3380c0f
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Notes de mise à jour de Primetime Ad Insertion 21.5.1

Les notes de mise à jour de l’Ad Insertion Primetime 21.x.x décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de l’Ad Insertion Primetime en 2021.

## Nouveautés de la version 21.5.1 de l’API

Lorsque :  Mercredi 26 mai 2021 de 3 h 30 à 06 h 30 EST

* Ajout de la prise en charge du type de segmentation obsolète 0x01 (UPID) pour les formats de repère basés sur SCTE.
* Ajout d’une nouvelle télémétrie pour les modifications à venir du tableau de bord.

## Améliorations et correctifs des versions précédentes

### Version 21.4.1

**Quand :** jeudi 22 avril 2021 de 02h00 à 5h00 EST

**Modifications**

* La limitation de la demande de session sera activée pour une protection contre les attaques DOS potentielles. Les sessions seront limitées à 10 requêtes par seconde, avec un plafond de 100 requêtes en file d’attente. Nous ne prévoyons aucun impact sur les lecteurs qui se comportent conformément aux spécifications HLS/DASH.
* Autres améliorations de maintenance et de sécurité

### Version 21.2.2

**Quand :** mardi 23 février 2021 de 1 h 00 à 4 h 00, heure de l’Est

**Modifications**

* Ajout de la prise en charge de l’insertion/synchronisation de flux EXT-X-IMAGE-STREAM-INF dans les flux HLS. La fonctionnalité est activée par le biais d’une configuration côté serveur. Contactez votre gestionnaire de compte technique pour activer la fonctionnalité.

### Version 21.2.1

**Quand :** mercredi 3 février 2021 de 1 h 00 à 4 h 00, heure de l’Est

**Modifications**

* Ajout de la prise en charge de l’optimisation de la sortie DASH : consolidation des noeuds basée sur le temps.

### Version 21.1.2

**Quand :** mardi 19 janvier 2021 de 00 h 30 à 08 h 30, heure de l’Est

**Modifications**

* Mise à jour de la maintenance : Mise à niveau des grappes de mémoire cache du serveur principal Ad Insertion Primetime.

### Version 21.1.1

**Quand :** mercredi 13 janvier 2021 de 01h00 à 04h00, heure de l’Est

**Modifications**

* Ajout de la prise en charge des mises à disposition d’affiliés pour les formats de repère basés sur SCTE35.

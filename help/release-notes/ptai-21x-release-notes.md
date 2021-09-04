---
title: Notes de mise à jour de PTAI 21.8.1
description: Les notes de mise à jour de l’API décrivent les nouveautés ou les modifications, les problèmes résolus et connus de l’Ad Insertion Primetime en 2021.
exl-id: 39a05f6d-431a-4416-81b1-21d82c0dbd69
source-git-commit: 97a192ed1d0ddc034f72a836a70293acfcca9881
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Notes de mise à jour de Primetime Ad Insertion 21.8.1

Les notes de mise à jour de l’Ad Insertion Primetime 21.x.x décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de l’Ad Insertion Primetime en 2021

<!---
Primetime Ad Insertion 21.9.1
When: Tuesday, September 7, 2021 from 02:30 AM to 05:30 AM EASTERN









What:  Primetime Ad Insertion 21.9.1

When:  Tuesday, September 7, 2021 from 02:30 AM to 05:30 AM Eastern Time

Changes:

* Updates to infrastructure components behind PTAI’s mediation and reporting components (Primetime Ads GUI)
-->

## Nouveautés de la version 21.8.1 de l’API

Lorsque : Mardi 24 août 2021 de 02h00 à 05h00, heure de l’Est

* Ajout de la prise en charge des diffusions DASH Live/Linéaire (VOD est déjà pris en charge).

## Améliorations et correctifs des versions précédentes

### Version 21.5.1

Lorsque :  Mercredi 26 mai 2021 de 3 h 30 à 6 h 30, heure de l’Est

**Modifications**

* Ajout de la prise en charge du type de segmentation obsolète 0x01 (UPID) pour les formats de repère basés sur SCTE.

* Ajout d’une nouvelle télémétrie pour les modifications à venir du tableau de bord.

### Version 21.4.1

**Quand :** jeudi 22 avril 2021 de 02h00 à 5h00, heure de l’Est

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

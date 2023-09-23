---
title: Notes de mise à jour de PTAI 21.11.1
description: Les notes de mise à jour de l’API décrivent les nouveautés ou les modifications, les problèmes résolus et connus de l’Ad Insertion Primetime en 2021.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Notes de mise à jour de Primetime Ad Insertion 21.11.1

Les notes de mise à jour de l’Ad Insertion Primetime 21.x.x décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de l’Ad Insertion Primetime en 2021.

## Nouveautés de l’API 21.11.1

Date : mardi 9 novembre 2021 de 1 h 30 à 4 h 30, heure de l’Est

* [!UICONTROL EXT-X-IMAGE-STREAM-INF] est maintenant configurable par zone.

* Roku Trick Play est entièrement pris en charge.

## Améliorations et correctifs des versions précédentes

### Version 21.10.1

Quand : mardi 12 octobre 2021 de 7 h 45 à 13 h 45, heure de l&#39;Est

* Serveurs consolidés, suppression des serveurs non productifs et non utiles.

### Version de maintenance de l’Ad Insertion Primetime

Quand : mardi 28 septembre 2021 de 5 h 00 à 6 h 00, heure de l’Est

* Mises à jour de la pile de l’équilibreur de charge d’AWS Elastic Load Balancer vers AWS Application Load Balancer pour des fonctionnalités et une évolutivité améliorées. Ces équilibreurs de charge sont utilisés pour acheminer le trafic de requête de publicité vers le serveur principal Auditude à partir de la couche Ad Insertion (SSAI/CSAI).

### Version 21.9.1

Quand : mardi 7 septembre 2021 de 02h30 à 05h30, heure de l’Est

* Mises à jour des composants d’infrastructure sous-jacents aux composants de médiation et de création de rapports de l’Ad Insertion Primetime (interface utilisateur graphique de Primetime Ads).

### Version 21.8.1

Date : mardi 24 août 2021 de 02h00 à 05h00, heure de l’Est

* Ajout de la prise en charge des diffusions DASH Live/Linéaire (VOD est déjà pris en charge).

### Version 21.5.1

Date : mercredi 26 mai 2021 de 3 h 30 à 06 h 30, heure de l’Est

**Modifications**

* Ajout de la prise en charge du type de segmentation obsolète 0x01 (UPID) pour les formats de repère basés sur SCTE.

* Ajout d’une nouvelle télémétrie pour les modifications à venir du tableau de bord.

### Version 21.4.1

**Lorsque :** Jeudi 22 avril 2021 de 02h00 à 5h00, heure de l’Est

**Modifications**

* La limitation de la demande de session sera activée pour une protection contre les attaques DOS potentielles. Les sessions seront limitées à 10 requêtes par seconde, avec un plafond de 100 requêtes en file d’attente. Nous ne prévoyons aucun impact sur les lecteurs qui se comportent conformément aux spécifications HLS/DASH.

* Autres améliorations de maintenance et de sécurité

### Version 21.2.2

**Lorsque :** Mardi 23 février 2021 de 1 h 00 à 4 h 00, heure de l’Est

**Modifications**

* Ajout de la prise en charge de l’insertion/synchronisation de flux EXT-X-IMAGE-STREAM-INF dans les flux HLS. La fonctionnalité est activée par le biais d’une configuration côté serveur. Contactez votre gestionnaire de compte technique pour activer la fonctionnalité.

### Version 21.2.1

**Lorsque :** Mercredi 3 février 2021 de 1 h 00 à 4 h 00, heure de l’Est

**Modifications**

* Ajout de la prise en charge de l’optimisation de la sortie DASH : consolidation des noeuds temporels.

### Version 21.1.2

**Lorsque :** Mardi 19 janvier 2021 de 00 h 30 à 08 h 30, heure de l’Est

**Modifications**

* Mise à jour de maintenance : mise à niveau des grappes de mémoire cache du serveur principal des Ad Insertion Primetime.

### Version 21.1.1

**Lorsque :** Mercredi 13 janvier 2021 de 01h00 à 04h00, heure de l’Est

**Modifications**

* Ajout de la prise en charge des mises à disposition d’affiliés pour les formats de repère basés sur SCTE35.

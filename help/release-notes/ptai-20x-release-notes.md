---
title: Notes de mise à jour de PTAI 20.5.1
description: Les notes de mise à jour de la version 20.5.1 de l’API décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus de l’insertion publicitaire dynamique Primetime en 2020.
translation-type: tm+mt
source-git-commit: 266b884707e9160d539a06fd089732ef8ade21ba
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Notes de mise à jour de Primetime Dynamic Ad Insertion 20.5.1

Les notes de mise à jour sur l’insertion dynamique des publicités 20.5.1 décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus dans l’insertion dynamique des publicités Primetime en 2020.

## Nouveautés de PTAI 20.5.1

**Lorsque :** Mardi 5 mai 2020 de 4 h à 5 h EST

* Correction d’un problème afin de s’assurer que les en-têtes CORS corrects sont fournis lors de l’envoi d’en-têtes If-Modified-Since.

* Correctifs de bogues sur le tableau de bord CRS.

* Mises à jour de maintenance.

## Nouveautés des versions précédentes

### Version 20.3.4

**Lorsque :** Mercredi 1er avril 2020 de 03h00 à 04h00 EST

* Correction d’un problème en raison duquel les sous-titres n’étaient pas synchronisés après l’insertion de publicités dans VOD/WebVTT.

* Mises à jour de sécurité.

### Version 20.3.3

**Lorsque :** Jeudi 26 mars 2020 de 3 h à 4 h EST

* Les réponses SSAI 4XX et 5XX fournissent désormais correctement des en-têtes liés à CORS, ce qui permet aux clients javascript/webview interdomaines de lire correctement les réponses d’erreur.

* Correction d’un problème lié aux en-têtes X-Forwarded-For, en raison duquel les adresses IPv6 n’étaient pas correctement codées dans l’URL lors de leur transmission aux serveurs d’annonces.

* Correction d’un problème lié aux flux audio CMAF/déuxed, en raison duquel les numéros EXT-X-MEDIA-SEQUENCE s’incrémentaient incorrectement dans certains scénarios.

### Version 20.1.3

**Lorsque :** Mardi 28 janvier 2020 de 2h00 à 3h00 EST

* **VMAP avec prise en charge FER pour nbc CueFormat**

   Convertissez des indices du flux FER en paramètres de remplacement de chronologie FW, lorsque `ptcueformat=nbc` ce flux est utilisé et qu’il s’agit d’un flux VOD avec des indices manifestes et des publicités intégrées.

* Expurger le champ user-agent dans l’en-tête HTTP avant de le transférer à des fournisseurs publicitaires tiers/CDN.

* Filtrez les caractères de contrôle/non imprimables (code ASCII &lt; 32) des en-têtes HTTP user-agent avant de les envoyer à Auditude et aux autres fournisseurs d’annonces, CDN. Auditude Ad-Call échouait pour ces en-têtes non valides.

* Purger les anciens objets V1 des groupes NetStorage pour que le nombre d’objets reste dans les limites sécurisées d’Akamai.

## Problèmes résolus

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche. Par exemple, ZD#xxxxx.

**PTAI 20.3.3**

* Problème avec les en-têtes X-Forwarded-For, où les adresses IPv6 n’étaient pas correctement codées en URL lors de leur transmission aux serveurs d’annonces.

* Problème avec les flux audio CMAF/déuxed, où dans certains scénarios les numéros EXT-X-MEDIA-SEQUENCE s&#39;incrémentent incorrectement dans certains scénarios

## Problèmes et limites connus

**PTAI 20.3.3**

Aucune nouvelle limitation n&#39;a été ajoutée.

---
title: Notes de mise à jour de PTAI 20.3.3
description: Les notes de mise à jour de la version 20.3.3 de l’IPAM décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus de l’insertion de publicités dynamiques Primetime en 2020.
translation-type: tm+mt
source-git-commit: ededb36a0b460fff4644a3716b36971ff9454c37

---


# Notes de mise à jour de Primetime Dynamic Ad Insertion 20.3.3

Les notes de mise à jour sur l’insertion dynamique des publicités 20.3.3 décrivent ce qui est nouveau ou modifié, les problèmes résolus et les problèmes connus dans l’insertion dynamique des publicités Primetime en 2020.

## Nouveautés de PTAI 20.3.3

**Lorsque :** Jeudi 26 mars 2020 de 3h00 à 4h00 EST

* Les réponses SSAI 4XX et 5XX fournissent désormais correctement les en-têtes liés à CORS, ce qui permet aux clients javascript/webview interdomaines de lire correctement les réponses d’erreur.

* Correction d’un problème avec les en-têtes X-Forwarded-For, en raison duquel les adresses IPv6 n’étaient pas correctement codées dans l’URL lors de leur transmission aux serveurs d’annonces.

* Correction d’un problème lié aux flux audio CMAF/démultiplexés, en raison duquel, dans certains cas, les nombres EXT-X-MEDIA-SEQUENCE s’incrémentaient incorrectement.

## Nouveautés des versions précédentes

### Version

**Lorsque :**

### Version

**Lorsque :**

## Problèmes résolus

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche. Par exemple, ZD#xxxxx.

**PTAI 20.3.3**

* Problème avec les en-têtes X-Forwarded-For, où les adresses IPv6 n’étaient pas correctement codées dans l’URL lors de leur transmission aux serveurs d’annonces.

* Problème avec les flux audio CMAF/démultiplexés, où, dans certains cas, les nombres EXT-X-MEDIA-SEQUENCE s’incrémentent incorrectement dans certains cas

## Problèmes et limites connus

**PTAI 20.3.3**

Aucune nouvelle limitation n’a été ajoutée.

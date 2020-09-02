---
title: Notes de mise à jour de PTAI 20.9.1
description: Les notes de mise à jour de la version 20.9.1 de l’API décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus de l’Ad Insertion dynamique Primetime en 2020.
translation-type: tm+mt
source-git-commit: 699e6a463bce4f7853406cb7fe529fb09f87ca92
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---


# Notes de mise à jour de l’Ad Insertion dynamique Primetime 20.9.1

Les notes de mise à jour de l’Ad Insertion dynamique version 20.9.1 décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de l’Ad Insertion dynamique Primetime en 2020.

## Nouveautés de PTAI 20.9.1

**Lorsque :** Mardi 1er septembre 2020 de 3h30 à 7h30, heure de l&#39;Est

**Modifications**

* Correction d’un problème pour les clients utilisant HLS/CMAF, en raison duquel EXT-X-MAP manquait parfois des jetons CDN ou des balises EXT-X-MAP parfois incorrectement déployées hors de la fenêtre DVR.

### Améliorations et correctifs des versions précédentes

#### Version 20.8.4

**Lorsque :** Mercredi 19 août 2020 de 03h30 à 07h30 heure de l&#39;Est

**Améliorations et correctifs**

Mises à jour de maintenance.

#### Version 20.8.1

**Lorsque :** Mardi 4 août 2020 de 3h00 à 6h00, heure de l&#39;Est

**Améliorations et correctifs**

Mises à jour de maintenance.

#### Version 20.7.1

**Lorsque :** Jeudi 9 juillet 2020 de 03h00 à 05h00, heure de l&#39;Est

**Nouvelles fonctionnalités et améliorations**

* Amélioration de SCTE35 pour utiliser soit les messages de Début/fin d&#39;annonce du fournisseur, soit les messages de Début/fin de rupture pour identifier le signal.

* Mise à jour de l’en-tête X-ADBE-AI-X1 avec des informations supplémentaires pour faciliter le dépannage.

* Amélioration de l’agrégation des mesures.

* Tableau de bord de la console SSAI amélioré pour le panneau Statistiques de session

#### Version 20.6.2

**Lorsque :** Jeudi 18 juin 2020 de 03:00 à 04:00 AM, heure de l&#39;Est

**Améliorations**

Amélioration de la synchronisation des flux pour les clients vidéo nécessitant une précision de milliseconde. Contactez l’assistance Adobe pour activer la précision en millisecondes pour `#EXT-X-PROGRAM-DATE-TIME tags`.

#### Version 20.6.1

**Lorsque :** Mardi 2 juin 2020 de 03h00 à 05h00, heure de l&#39;Est

**Nouvelles fonctionnalités**

Contactez l’assistance Adobe pour activer les nouvelles fonctionnalités suivantes via la configuration côté serveur :

* Manipulation du manifeste : Les segments HLS et les URL de ressources peuvent désormais être transformés entre HTTP et HTTPS afin d’améliorer les performances en réduisant les poignées de main TLS sur les requêtes principales. Il peut également être utilisé pour unifier des fragments de publicités/de contenu sur les mêmes CDN.

* VOD de forme longue : Amélioration des API pour maintenir la session en vie avec les ressources VOD de forme longue.

**Correctifs**

* Correction d’un problème en raison duquel les fragments WebVTT étaient toujours demandés sous le protocole http, quel que soit le protocole d’origine demandé.

* Correction d’un problème en raison duquel les balises EXT-X-DISCONTINUITY étaient supprimées du haut de la liste de lecture lors du passage des publicités au contenu. Contactez l’assistance Adobe pour activer ce correctif.

#### Version 20.5.1

**Lorsque :** Mardi 5 mai 2020 de 4 h à 5 h, heure de l&#39;Est

* Correction d’un problème afin de s’assurer que les en-têtes CORS corrects sont fournis lors de l’envoi d’en-têtes If-Modified-Since.

* Correctifs de bogues sur le tableau de bord CRS.

* Mises à jour de maintenance.

#### Version 20.3.4

**Lorsque :** Mercredi 1er avril 2020 de 03h00 à 04h00, heure de l&#39;Est

* Correction d’un problème en raison duquel les sous-titres n’étaient pas synchronisés après l’insertion de publicités dans VOD/WebVTT.

* Mises à jour de sécurité.

#### Version 20.3.3

**Lorsque :** Jeudi 26 mars 2020 de 03h00 à 04h00, heure de l&#39;Est

* Les réponses SSAI 4XX et 5XX fournissent désormais correctement des en-têtes liés à CORS, ce qui permet aux clients de vues Web javascript interdomaines de lire correctement les réponses d’erreur.

* Correction d’un problème lié aux en-têtes X-Forwarded-For, en raison duquel les adresses IPv6 n’étaient pas correctement codées dans l’URL lors de leur transmission aux serveurs d’annonces.

* Correction d’un problème lié aux flux audio CMAF/déuxed, en raison duquel les numéros EXT-X-MEDIA-SEQUENCE s’incrémentaient incorrectement dans certains scénarios.

#### Version 20.3.2

**Lorsque :** Mercredi 11 mars 2020 de 05h30 à 07h00, heure de l&#39;Est

* Améliorations de la gestion du signal SCTE35.

* Mises à jour de maintenance.

#### Version 20.3.1

**Lorsque :** Jeudi 5 mars 2020 de 02h30 à 04h30, heure de l&#39;Est

* Amélioration des performances :

   * Prise en charge Ajoutée du cache pour les manifestes m3u8 maître/média. Ces manifestes répondent maintenant à Cache-Control : en-têtes publics et Max-Age, qui peuvent souvent améliorer les performances du début vidéo.

   * Prise en charge Ajoutée pour forcer la récupération des éléments créatifs https sur http, ce qui peut également améliorer les performances des débuts vidéo.

* Correctifs de sécurité et de maintenance.

#### Version 20.2.1

**Lorsque :** Jeudi 13 février 2020 de 4 h 30 à 05 h 30, heure de l&#39;Est

* Prise en charge Ajoutée de l’assemblage de ressources publicitaires qui contiennent plusieurs flux audio uniquement en fonction de la langue/du codec/du débit.
* Améliorations mineures des performances et mises à jour de maintenance.

#### Version 20.1.3

**Lorsque :** Mardi 28 janvier 2020 de 2h00 à 3h00, heure de l&#39;Est

* **VMAP avec prise en charge FER pour nbc CueFormat**

   Convertissez des indices du flux FER en paramètres de remplacement de chronologie FW, lorsque `ptcueformat=nbc` ce flux est utilisé et qu’il s’agit d’un flux VOD avec des indices manifestes et des publicités intégrées.

* Expurger le champ user-agent dans l’en-tête HTTP avant de le transférer à des fournisseurs publicitaires tiers/CDN.

* Filtrez les caractères de contrôle/non imprimables (code ASCII &lt; 32) des en-têtes HTTP user-agent avant de les envoyer à Auditude et aux autres fournisseurs d’annonces, CDN. Auditude Ad-Call échouait pour ces en-têtes non valides.

* Purger les anciens objets V1 des groupes NetStorage pour que le nombre d’objets reste dans les limites sécurisées d’Akamai.

#### Version 20.1.2 (Correctif)

**Lorsque :** Lundi 20 janvier 2020 de 02h00 à 03h00, heure de l&#39;Est

* Mises à jour de maintenance.

#### Version 20.1.1

**Lorsque :** Mercredi 15 janvier 2020 de 4 h à 05 h, heure de l&#39;Est

* Le service de reconditionnement d’images offre désormais une insertion publicitaire plus rapide en bloquant automatiquement la liste des créatifs malformés.

* Prise en charge de la phase 1 Ajoutée pour le nouveau format de repère SCTE 35 dans l&#39;insertion de publicités côté serveur.

* Mises à niveau de maintenance.

## Problèmes résolus {#Resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche. Par exemple, `ZD#xxxxx`.

**PITA 20.9.1**

* Correction d’un problème pour les clients utilisant HLS/CMAF, en raison duquel EXT-X-MAP manquait parfois des jetons CDN ou des balises EXT-X-MAP parfois incorrectement déployées hors de la fenêtre DVR.

**PITA 20.6.1**

* `WebVTT` les fragments étaient toujours demandés dans le protocole http, quel que soit le protocole original demandé.

* `EXT-X-DISCONTINUITY` sont supprimées du haut de la liste de lecture lors du passage des publicités au contenu. Contactez l’assistance Adobe pour activer ce correctif.

**PITA 20.5.1**

* Problèmes d’en-têtes CORS lors de l’envoi d’en-têtes If-Modified-Since.

* Questions relatives au tableau de bord CRS.

**PTAI 20.3.4**

* Problème en raison duquel les sous-titres n’étaient pas synchronisés après l’insertion de publicités dans VOD/WebVTT.

**PTAI 20.3.3**

* Problème avec les en-têtes X-Forwarded-For, où les adresses IPv6 n’étaient pas correctement codées en URL lors de leur transmission aux serveurs d’annonces.

* Problème avec les flux audio CMAF/déuxed, où dans certains scénarios les numéros EXT-X-MEDIA-SEQUENCE s&#39;incrémentent incorrectement dans certains scénarios

## Problèmes et limites connus

**PTAI 20.3.3**

Aucune nouvelle limitation n&#39;a été ajoutée.

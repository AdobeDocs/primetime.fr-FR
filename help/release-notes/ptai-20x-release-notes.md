---
title: Notes de mise à jour de PTAI 20.12.1
description: Les notes de mise à jour de l’API décrivent les nouveautés ou les modifications, les problèmes résolus et connus de l’Ad Insertion Primetime en 2020.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1081'
ht-degree: 0%

---

# Notes de mise à jour de Primetime Ad Insertion 20.12.1

Les notes de mise à jour de l’Ad Insertion Primetime 20.12.1 décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de l’Ad Insertion Primetime en 2020.

## Nouveautés de l’API 20.12.1

**Lorsque :** Mardi 8 décembre 2020 de 1 h à 4 h, heure de l’Est

**Modifications**

* Comprend un correctif pour résoudre les problèmes de connectivité client intermittente (5xx) dans l’Ad Insertion Primetime rencontré le 30 novembre 2020.

## Améliorations et correctifs des versions précédentes

### Version 20.11.1

**Lorsque :** Jeudi 5 novembre 2020 de 14 h à 05 h, heure de l’Est

**Modifications**

* Mises à jour de maintenance.

### Version 20.10.2

**Lorsque :** Jeudi 29 octobre 2020 de 12h01 à 6h00, heure de l’Est

**Modifications**

* Mises à jour de maintenance.

### Version 20.10.1

**Lorsque :** Mardi 13 octobre 2020 de 3 h à 7 h, heure de l’Est

**Modifications**

* Mises à jour de maintenance.

### Version 20.9.3

**Lorsque :** Mercredi 30 septembre 2020 de 3 h 30 à 6 h 30, heure de l’Est

**Modifications**

* Ajout du paramètre d’API du Bootstrap `ptparallelstream`. Cela permet aux clients disposant de lecteurs qui demandent des diffusions audio ou vidéo compressées en parallèle pour s’assurer que les publicités dans les pistes audio et vidéo sont cohérentes. Définissez la valeur du paramètre sur true pour activer cette fonction ou omettez de la désactiver.

### Version 20.9.2

**Lorsque :** Mardi 15 septembre 2020 de 3 h 30 à 6 h 30, heure de l’Est

**Améliorations**

* Prise en charge de l’inclusion de types de publicités non linéaires à l’aide de `EXT-X-MARKER` balises.
Pour plus d’informations ou pour activer cette fonctionnalité, contactez votre représentant de l’assistance technique.

* Prise en charge de la limitation du temps total de résolution des publicités si les fournisseurs mettent trop de temps à répondre. Pour activer la limitation, définissez le paramètre de l’API de démarrage. `ptadtimeout` en millisecondes.

  >[!NOTE]
  >
  >Ce délai d’expiration s’applique uniquement aux demandes d’annonces, et non aux demandes d’annonces créatives.

### Version 20.9.1

**Lorsque :** Mardi 1er septembre 2020 de 3 h 30 à 7 h 30, heure de l’Est

**Modifications**

* Correction d’un problème pour les clients utilisant HLS/CMAF, en raison duquel EXT-X-MAP manquait parfois des jetons CDN ou des balises EXT-X-MAP parfois incorrectement déployées hors de la fenêtre DVR.

### Version 20.8.4

**Lorsque :** Mercredi 19 août 2020 de 3 h 30 à 7 h 30, heure de l’Est

**Améliorations et correctifs**

Mises à jour de maintenance.

### Version 20.8.1

**Lorsque :** Mardi 4 août 2020 de 3 h 00 à 6 h 00, heure de l’Est

**Améliorations et correctifs**

Mises à jour de maintenance.

### Version 20.7.1

**Lorsque :** Jeudi 9 juillet 2020 de 3 h à 5 h, heure de l’Est

**Nouvelles fonctionnalités et améliorations**

* Amélioration de SCTE35 pour utiliser soit les messages de début/fin de publicité du fournisseur, soit les messages de début/fin de la coupure pour identifier le signal.

* Mise à jour de l’en-tête X-ADBE-AI-X1 avec des informations supplémentaires pour faciliter le dépannage.

* Agrégation des mesures améliorée.

* Tableau de bord de la console SSAI amélioré pour le panneau Statistiques de session

### Version 20.6.2

**Lorsque :** Jeudi 18 juin 2020 de 3 h à 4 h, heure de l’Est

**Améliorations**

Amélioration de la synchronisation des flux pour les clients vidéo qui nécessitent une précision en millisecondes. Contactez l’assistance Adobe pour activer la précision en millisecondes pour `#EXT-X-PROGRAM-DATE-TIME tags`.

### Version 20.6.1

**Lorsque :** Mardi 2 juin 2020 de 3 h à 5 h, heure de l’Est

**Nouvelles fonctionnalités**

Contactez l’assistance Adobe pour activer les nouvelles fonctionnalités suivantes via la configuration côté serveur :

* Manipulation de manifeste : les URL de segment et de ressource HLS peuvent désormais être transformées entre HTTP et HTTPS afin d’améliorer les performances en réduisant les poignées de main TLS sur les requêtes principales. Il peut également être utilisé pour unifier les fragments de contenu/publicités sur les mêmes CDN.

* Long Form VOD : API améliorées pour maintenir la persistance de session avec des ressources VOD de formulaire long.

**Correctifs**

* Correction d’un problème en raison duquel les fragments WebVTT étaient toujours demandés sous le protocole http, quel que soit le protocole d’origine demandé.

* Correction d’un problème en raison duquel les balises EXT-X-DISCONTINUITY étaient supprimées du haut de la liste de lecture lors du passage des publicités au contenu. Contactez l’assistance Adobe pour activer ce correctif.

### Version 20.5.1

**Lorsque :** Mardi 5 mai 2020 de 4 h à 5 h (heure de l’Est)

* Correction d’un problème pour s’assurer que les en-têtes CORS corrects sont fournis lors de l’envoi des en-têtes If-Modified-Since .

* Correctifs de bogues sur le tableau de bord CRS.

* Mises à jour de maintenance.

### Version 20.3.4

**Lorsque :** Mercredi 1er avril 2020 de 3 h à 4 h (heure de l’Est)

* Correction d’un problème en raison duquel les sous-titres n’étaient pas synchronisés après l’insertion de publicités dans VOD/WebVTT.

* Mises à jour de sécurité.

### Version 20.3.3

**Lorsque :** Jeudi 26 mars 2020 de 3 h à 4 h, heure de l’Est

* Les réponses SSAI 4XX et 5XX fournissent désormais correctement des en-têtes liés à CORS, ce qui permet aux clients de webview javascript interdomaines de lire correctement les réponses d’erreur.

* Correction d’un problème lié aux en-têtes X-Forwarded-For, en raison duquel les adresses IPv6 n’étaient pas correctement encodées URL lors de leur transmission aux serveurs d’annonces.

* Correction d’un problème lié aux diffusions audio CMAF/demuxed, en raison duquel, dans certains scénarios, les numéros EXT-X-MEDIA-SEQUENCE s’incrémentaient incorrectement.

### Version 20.3.2

**Lorsque :** Mercredi 11 mars 2020 de 5h30 à 7h00, heure de l’Est

* Améliorations de la gestion des signaux SCTE35.

* Mises à jour de maintenance.

### Version 20.3.1

**Lorsque :** Jeudi 5 mars 2020 de 02h30 à 04h30, heure de l’Est

* Amélioration des performances :

   * Ajout de la prise en charge du cache pour les manifestes m3u8 principal/multimédia. Ces manifestes répondent désormais aux en-têtes Cache-Control: public et Max-Age, qui peuvent souvent améliorer les performances de démarrage vidéo.

   * Ajout de la prise en charge de la récupération forcée des éléments créatifs https sur http, ce qui peut également améliorer les performances de démarrage vidéo.

* Correctifs de sécurité et de maintenance.

### Version 20.2.1

**Lorsque :** Jeudi 13 février 2020 de 4 h 30 à 5 h 30, heure de l’Est

* Ajout de la prise en charge du regroupement de ressources publicitaires qui contiennent plusieurs flux audio uniquement basés sur la langue/le codec/bitrate.
* Améliorations mineures des performances et mises à jour de maintenance.

### Version 20.1.3

**Lorsque :** Mardi 28 janvier 2020 de 02h00 à 03h00, heure de l’Est

* **VMAP avec prise en charge FER pour nbc CueFormat**

  Convertissez des signaux du flux FER en paramètres de remplacement de la chronologie FW, lorsque `ptcueformat=nbc` est utilisé et le flux est un flux VOD avec indices manifestes et publicités nues.

* assainir le champ agent-utilisateur dans l’en-tête HTTP avant de le transférer à des fournisseurs de publicités/réseaux de diffusion de contenu tiers ;

* Filtrez les caractères de contrôle/non imprimables (code ASCII &lt; 32) des en-têtes HTTP de l’agent utilisateur avant de les envoyer à des Auditude et à d’autres fournisseurs de publicités, CDN. L’appel publicitaire Auditude échouait pour ces en-têtes non valides.

* Purge des anciens objets V1 des groupes NetStorage afin que le nombre d’objets reste dans les limites sécurisées d’Akamai.

### Version 20.1.2 (correctif)

**Lorsque :** Lundi 20 janvier 2020 de 02h00 à 03h00, heure de l’Est

* Mises à jour de maintenance.

### Version 20.1.1

**Lorsque :** Mercredi 15 janvier 2020 de 4 h à 5 h (heure de l’Est)

* Le service de remarketing créatif offre désormais une insertion de publicités plus rapide en bloquant automatiquement les créatifs mal formés.

* Ajout de la prise en charge de la phase 1 pour le nouveau format de repère SCTE 35 dans l’insertion de publicités côté serveur.

* Mises à niveau de la maintenance.

## Problèmes résolus {#Resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche. Par exemple : `ZD#xxxxx`.

**PTAI 20.9.1**

* Correction d’un problème pour les clients utilisant HLS/CMAF, en raison duquel EXT-X-MAP manquait parfois des jetons CDN ou des balises EXT-X-MAP parfois incorrectement déployées hors de la fenêtre DVR.

**PTAI 20.6.1**

* `WebVTT` les fragments étaient toujours demandés sous le protocole http, quel que soit le protocole d’origine demandé.

* `EXT-X-DISCONTINUITY` les balises sont supprimées de la partie supérieure de la liste de lecture lors du passage des publicités au contenu. Contactez l’assistance Adobe pour activer ce correctif.

**PTAI 20.5.1**

* Problèmes avec les en-têtes CORS lors de l’envoi des en-têtes If-Modified-Since .

* Problèmes dans le tableau de bord CRS.

**PTAI 20.3.4**

* Problème en raison duquel les sous-titres n’étaient pas synchronisés après l’insertion de publicités dans VOD/WebVTT.

**PTAI 20.3.3**

* Problème avec les en-têtes X-Forwarded-For, où les adresses IPv6 n’étaient pas correctement codées URL lors de leur transmission aux serveurs de publicités.

* Problème avec les flux audio CMAF/demuxed, où dans certains scénarios les numéros EXT-X-MEDIA-SEQUENCE s’incrémentent incorrectement dans certains scénarios

## Problèmes connus et limites

**PTAI 20.10.1**

Aucune nouvelle limitation n’a été ajoutée.

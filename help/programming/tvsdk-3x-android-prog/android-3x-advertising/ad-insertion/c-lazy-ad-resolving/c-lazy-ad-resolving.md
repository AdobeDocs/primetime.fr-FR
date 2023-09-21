---
description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend que la lecture démarre. Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage. La résolution différée des publicités a considérablement changé dans la version 3.0. Dans le chargement différé de publicités avant la version 3.0, la résolution de la publicité a été divisée en deux étapes, résolvant uniquement les publicités pré-restauration avant l’état PRÉPARÉ , et les publicités mid-rolls et post-rolls après l’état PRÉPARÉ . Cela a changé et les coupures publicitaires sont désormais résolues à un intervalle spécifié avant la position de la coupure publicitaire.
keywords: Lazy;résolution de publicité;chargement de publicité
title: Résolution de publicités juste à temps
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# Présentation {#just-in-time-ad-resolving-overview}

La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend que la lecture démarre. Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage. La résolution différée des publicités a considérablement changé dans la version 3.0. Dans le chargement différé de publicités avant la version 3.0, la résolution de la publicité a été divisée en deux étapes, résolvant uniquement les publicités pré-restauration avant l’état PRÉPARÉ , et les publicités mid-rolls et post-rolls après l’état PRÉPARÉ . Cela a changé et les coupures publicitaires sont désormais résolues à un intervalle spécifié avant la position de la coupure publicitaire.

* Processus de base de résolution et de chargement des publicités :

   1. TVSDK télécharge un manifeste (liste de lecture) et *résout* toutes les publicités.
   1. TVSDK *chargements* toutes les publicités et les place dans la chronologie.
   1. TVSDK déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.

  Le lecteur utilise les URL du manifeste pour obtenir le contenu de la publicité (éléments créatifs), s’assure que le contenu de la publicité est dans un format que TVSDK peut lire et que TVSDK place les publicités dans la chronologie. Ce processus de base de résolution et de chargement des publicités peut entraîner un délai inacceptable pour un utilisateur qui attend de lire son contenu, en particulier si le manifeste contient plusieurs URL d’annonce.

* *Chargement différé des publicités*:

   1. TVSDK télécharge une liste de lecture et *résout* toutes les publicités.
   1. TVSDK *chargements* publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   1. TVSDK *chargements* les publicités restantes et les place dans la chronologie au fur et à mesure de la lecture.

  Cette fonction améliore le processus de base en plaçant le lecteur dans l’état PRÉPARÉ avant le chargement de toutes les publicités.

* *Résolution de publicités différées*:

   1. TVSDK télécharge la liste de lecture.
   1. TVSDK résout et charge toutes les publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   1. TVSDK résout et chacune des coupures publicitaires restantes individuellement en fonction du calcul suivant :

      `AdvertisingMetadata::getDelayAdLoadingTolerance() + PlayBufferTime::playBufferTime + the value defined in EXT-X-TARGETDURATION`

      Par défaut, pour le contenu avec une durée cible de 6 secondes, cette durée est de 5,0 + 30,0 + 6,0 secondes (41 secondes).

   1. Si une coupure publicitaire se produit dans les 10 secondes suivant le début de la position, elle est résolue avec les publicités preroll avant l’état PRÉPARÉ .

>[!IMPORTANT]
>
>**Facteurs à prendre en compte avec la résolution de publicités différée :**
>
>* La résolution différée des publicités n’est prise en charge que pour les flux VOD avec les modes SERVER_MAP et MANIFEST_CUES.
>* La résolution des publicités différées n’est pas activée par défaut. Si cette option est désactivée, toutes les publicités sont résolues sur les flux VOD avant le début de la lecture.
>* La résolution différée des publicités est incompatible avec la fonction Instant On . Pour plus d’informations sur Instant On, voir Instant On.
>* Avec la résolution de publicités différées, lors d’une recherche vers l’avant au-dessus d’une coupure publicitaire, la coupure publicitaire la plus proche de la position de recherche sera résolue pendant la recherche.
>* Avec la résolution des publicités différées, si plusieurs coupures publicitaires existent en même temps (VMAP), elles seront résolues en même temps.
>* Il n’est pas recommandé de réduire la valeur de *setDelayAdLoadingTolérance() *en dessous de la valeur par défaut (5 secondes). Ce faisant, le lecteur pourrait &quot;mettre en mémoire tampon&quot; inutilement.
>* La résolution des publicités différées n’a aucune incidence sur les publicités preroll.
>* La résolution des publicités différée est actuellement prise en charge avec le module Auditude-Plugin. Il est recommandé de ne pas définir *setDelayAdLoading* sur true si vous utilisez un résolveur personnalisé.
>

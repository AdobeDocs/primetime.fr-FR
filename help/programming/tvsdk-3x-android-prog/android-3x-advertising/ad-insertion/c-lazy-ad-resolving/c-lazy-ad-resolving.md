---
description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. Les fonctions Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage. La résolution des publicités a considérablement changé dans la version 3.0. Lors du chargement des publicités différées avant la version 3.0, la résolution des publicités était divisée en deux étapes, ce qui ne permettait de résoudre que les publicités pré-rouleaux avant l’état PRÉPARÉ, et les publicités moyennes et post-rolls après l’état PRÉPARÉ. Ceci a changé et les coupures publicitaires sont maintenant résolues à un intervalle spécifié avant la position de la coupure publicitaire.
keywords: Lazy;Ad resolving;Ad loading
seo-description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. Les fonctions Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage. La résolution des publicités a considérablement changé dans la version 3.0. Lors du chargement des publicités différées avant la version 3.0, la résolution des publicités était divisée en deux étapes, ce qui ne permettait de résoudre que les publicités pré-rouleaux avant l’état PRÉPARÉ, et les publicités moyennes et post-rolls après l’état PRÉPARÉ. Ceci a changé et les coupures publicitaires sont maintenant résolues à un intervalle spécifié avant la position de la coupure publicitaire.
seo-title: Résolution de la publicité juste à temps
title: Résolution de la publicité juste à temps
uuid: 77028f6e-7e53-45d1-bcc0-54f8224d6d18
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Présentation {#just-in-time-ad-resolving-overview}

La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. Les fonctions Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage. La résolution des publicités a considérablement changé dans la version 3.0. Lors du chargement des publicités différées avant la version 3.0, la résolution des publicités était divisée en deux étapes, ce qui ne permettait de résoudre que les publicités pré-rouleaux avant l’état PRÉPARÉ, et les publicités moyennes et post-rolls après l’état PRÉPARÉ. Ceci a changé et les coupures publicitaires sont maintenant résolues à un intervalle spécifié avant la position de la coupure publicitaire.

* Processus de base de résolution et de chargement des publicités :

   1. TVSDK télécharge un manifeste (playlist) et *résout* toutes les publicités.
   1. TVSDK *charge* toutes les publicités et les place sur la chronologie.
   1. TVSDK déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   Le lecteur utilise les URL du manifeste pour obtenir le contenu de la publicité (éléments créatifs), s’assure que le contenu de la publicité est dans un format lisible par TVSDK et TVSDK place les publicités sur la chronologie. Ce processus de base de résolution et de chargement des publicités peut provoquer un délai inacceptable pour un utilisateur attendant de lire son contenu, en particulier si le manifeste contient plusieurs URL de publicité.

* *Chargement* publicitaire différé :

   1. TVSDK télécharge une liste de lecture et *résout* toutes les publicités.
   1. TVSDK *charge* les publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   1. TVSDK *charge* les publicités restantes et les place sur la chronologie au fur et à mesure de la lecture.
   Cette fonction améliore le processus de base en plaçant le lecteur dans l’état PRÉPARÉ avant le chargement de toutes les publicités.

* *Résolution* des publicités relayées :

   1. TVSDK télécharge la liste de lecture.
   1. TVSDK résout et charge toutes les publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   1. TVSDK résout et interrompt chacune des publicités restantes individuellement en fonction du calcul suivant :

      `AdvertisingMetadata::getDelayAdLoadingTolerance() + PlayBufferTime::playBufferTime + the value defined in EXT-X-TARGETDURATION`

      Par défaut, pour le contenu d’une Cible de 6 secondes, cette valeur est de 5,0 + 30,0 + 6,0 secondes (41 secondes).

   1. Si une coupure publicitaire survient dans les 10 secondes qui suivent la position du début, elle est résolue avec les publicités preroll avant l’état PRÉPARÉ.

>[!IMPORTANT]
>
>**Facteurs à prendre en compte avec la résolution de publicités diffuses :** >
>* La résolution des publicités différées n&#39;est prise en charge que pour les flux VOD avec les modes SERVER_MAP et MANIFEST_CUES.
>* La résolution des publicités différées n’est pas activée par défaut. Si cette option est désactivée, toutes les publicités sont résolues dans les flux VOD avant les débuts de lecture.
>* La résolution des publicités différées est incompatible avec la fonction Instant On. Pour plus d’informations sur Instant On, voir Instant On.
>* Avec la résolution de publicités différées, tout en recherchant une coupure publicitaire ultérieure, la coupure publicitaire la plus proche de la position de recherche sera résolue pendant la recherche.
>* Avec la résolution des publicités différées, s’il existe plusieurs coupures publicitaires en même temps (VMAP), elles seront résolues en même temps.
>* Il n’est pas recommandé de réduire la valeur de *setDelayAdLoadingTolerance() *en dessous de la valeur par défaut (5 secondes). Ce faisant, le lecteur pourrait &quot;mettre en mémoire tampon&quot; inutilement.
>* La résolution des publicités différées n’a aucune incidence sur les publicités preroll.
>* La résolution des publicités différées est actuellement prise en charge avec le module externe Auditude. Il est recommandé de ne pas définir ** setDelayAdLoadinging sur true si vous utilisez un résolveur personnalisé.
>



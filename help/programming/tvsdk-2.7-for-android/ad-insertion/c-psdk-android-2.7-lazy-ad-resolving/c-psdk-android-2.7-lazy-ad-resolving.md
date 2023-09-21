---
description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend que la lecture démarre. Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.
keywords: Lazy;résolution de publicité;chargement de publicité
title: Résolution des publicités différées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Présentation {#lazy-ad-resolving}

La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend que la lecture démarre. Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.

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
   1. TVSDK résout et charge les publicités restantes et les place dans la chronologie au fur et à mesure de la lecture.

  La résolution des publicités différées s’appuie sur le chargement différé des publicités pour permettre un démarrage encore plus rapide. Une fois que TVSDK a placé des publicités preroll, il déplace le lecteur dans l’état PRÉPARÉ, puis résout des publicités supplémentaires et les place dans la chronologie.

>[!IMPORTANT]
>
>Facteurs à prendre en compte avec la résolution de publicités différée :
>
>* La résolution des publicités différées est activée par défaut. Si vous la désactivez, toutes les publicités sont résolues avant le début de la lecture.
>* La résolution différée des publicités n’autorise pas la recherche ou le trickplay tant que toutes les publicités ne sont pas résolues :
>
>    * Le lecteur doit attendre que la variable `kEventAdResolutionComplete` avant d’autoriser la recherche ou le jeu vidéo.
>    * Si l’utilisateur tente d’effectuer des opérations de recherche ou de lecture pendant que les publicités sont toujours en cours de résolution, TVSDK renvoie la variable `kECLazyAdResolutionInProgress` erreur.
>    * Si nécessaire, le lecteur doit mettre à jour la barre de défilement, *after* recevoir le `kEventAdResolutionComplete` .
>
>* La résolution de publicités différée est réservée à VOD uniquement. Il ne fonctionnera pas avec les flux LIVE.
>* La résolution différée des publicités est incompatible avec la fonction *Instant activé* fonction .
>
>  Pour plus d’informations sur Instant On, voir Instant on .
>
>* Bien que la résolution différée des publicités entraîne un démarrage de la lecture beaucoup plus rapide, si une coupure publicitaire se produit dans les 60 premières secondes de lecture, elle risque de ne pas être résolue.
>* La résolution différée des publicités n’a aucune incidence sur les publicités preroll.

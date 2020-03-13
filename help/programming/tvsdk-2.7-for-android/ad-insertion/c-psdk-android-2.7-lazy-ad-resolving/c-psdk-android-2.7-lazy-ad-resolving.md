---
description: La résolution des publicités et le chargement des publicités peuvent entraîner un délai inacceptable pour un utilisateur qui attend que la lecture soit . Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.
keywords: Lazy;Ad resolving;Ad loading
seo-description: La résolution des publicités et le chargement des publicités peuvent entraîner un délai inacceptable pour un utilisateur qui attend que la lecture soit . Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.
seo-title: Résolution des publicités irrégulières
title: Résolution des publicités irrégulières
uuid: cf9ba788-b83f-43aa-94c4-db391d92a77b
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#lazy-ad-resolving}

La résolution des publicités et le chargement des publicités peuvent entraîner un délai inacceptable pour un utilisateur qui attend que la lecture soit . Les fonctionnalités Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.

* Processus de base de résolution et de chargement des publicités :

   1. TVSDK télécharge un manifeste (playlist) et *résout* toutes les publicités.
   1. TVSDK *charge* toutes les publicités et les place dans la chronologie.
   1. TVSDK déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   Le lecteur utilise les URL du manifeste pour obtenir le contenu de la publicité (créatifs), s’assure que le contenu de la publicité est dans un format lisible par TVSDK et que TVSDK place les publicités sur la chronologie. Ce processus de base de résolution et de chargement des publicités peut entraîner un délai inacceptable pour un utilisateur qui attend de lire son contenu, en particulier si le manifeste contient plusieurs URL de publicité.

* *Chargement* de publicités différé :

   1. TVSDK télécharge une liste de lecture et *résout* toutes les publicités.
   1. TVSDK *charge* les publicités preroll, déplace le lecteur vers l’état PRÉPARÉ et la lecture du contenu commence.
   1. TVSDK *charge* les publicités restantes et les place sur la chronologie au fur et à mesure de la lecture.
   Cette fonctionnalité améliore le processus de base en plaçant le lecteur dans l’état PRÉPARÉ avant le chargement de toutes les publicités.

* *Résolution* des publicités irrégulières :

   1. TVSDK télécharge la liste de lecture.
   1. TVSDK résout et charge toutes les publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
   1. TVSDK résout et charge les publicités restantes et les place sur la chronologie au fur et à mesure de la lecture.
   La résolution des publicités relayées s’appuie sur le chargement des publicités relayées pour permettre une  encore plus rapide. Une fois que TVSDK a placé des publicités preroll, il déplace le lecteur dans l’état PRÉPARÉ, puis résout les publicités supplémentaires et les place dans la chronologie.

>[!IMPORTANT]
>
>Facteurs à prendre en compte dans la résolution des publicités différentielles :
>
>* La résolution des publicités différées est activée par défaut. Si vous la désactivez, toutes les publicités sont résolues avant le  de lecture.
>* La résolution de publicités diffuses n’autorise la recherche ou le trickplay qu’une fois toutes les publicités résolues :>
   >    * Le joueur doit attendre la  du `kEventAdResolutionComplete` avant de permettre la recherche ou le jeu.
   >    * Si l’utilisateur tente d’effectuer des opérations de recherche ou de lecture vidéo pendant que les publicités sont toujours en cours de résolution, TVSDK renvoie l’ `kECLazyAdResolutionInProgress` erreur.
   >    * Si nécessaire, le lecteur doit mettre à jour la barre de défilement, *après* avoir reçu le  `kEventAdResolutionComplete` du.
>
>* La résolution des publicités différées est réservée aux VOD uniquement. Il ne fonctionnera pas avec les flux LIVE.
>* La résolution des publicités différées est incompatible avec la fonction *Instant on* .
>
>  

Pour plus d’informations sur Instant on, voir Instant on .
>
>* Bien que la résolution de publicités différées entraîne un démarrage de la lecture beaucoup plus rapide, si une coupure publicitaire survient dans les 60 premières secondes de la lecture, elle risque de ne pas être résolue.
>* La résolution des publicités diffuses n’affecte pas les publicités preroll.
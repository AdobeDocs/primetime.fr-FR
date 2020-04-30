---
description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. Les fonctions Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.
keywords: Lazy;Ad resolving;Ad loading
seo-description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. Les fonctions Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.
seo-title: Résolution de publicités diffuses
title: Résolution de publicités diffuses
uuid: cf9ba788-b83f-43aa-94c4-db391d92a77b
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#lazy-ad-resolving}

La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. Les fonctions Lazy Ad Loading et Lazy Ad Resolving peuvent réduire ce délai de démarrage.

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
   1. TVSDK résout et charge les publicités restantes et les place sur la chronologie au fur et à mesure de la lecture.
   La résolution des publicités relayées s’appuie sur le chargement des publicités relayées pour permettre un début encore plus rapide. Une fois que TVSDK a placé des publicités preroll, il déplace le lecteur dans l’état PRÉPARÉ, puis résout des publicités supplémentaires et les place dans la chronologie.

>[!IMPORTANT]
>
>Facteurs à prendre en compte avec la résolution de publicités diffuses :
>
>* La résolution des publicités différées est activée par défaut. Si vous la désactivez, toutes les publicités sont résolues avant les débuts de lecture.
>* La résolution des publicités différées n’autorise la recherche ou le trickplay qu’une fois toutes les publicités résolues :>
   >    * Le joueur doit attendre le `kEventAdResolutionComplete` événement avant de permettre la recherche ou le jeu de ficelles.
   >    * Si l’utilisateur tente d’effectuer des opérations de recherche ou de lecture vidéo pendant que les publicités sont toujours en cours de résolution, TVSDK renvoie l’ `kECLazyAdResolutionInProgress` erreur.
   >    * Si nécessaire, le lecteur doit mettre à jour la barre de défilement *après* avoir reçu le `kEventAdResolutionComplete` événement.
>
>* La résolution des publicités différées est réservée à VOD uniquement. Il ne fonctionnera pas avec les flux LIVE.
>* La résolution des publicités différées est incompatible avec la fonction *Instant On* .
>
>  

Pour plus d’informations sur Instant on, voir Instant on .
>
>* Bien que la résolution des publicités différées entraîne un démarrage de la lecture beaucoup plus rapide, si une coupure publicitaire se produit au cours des 60 premières secondes de lecture, elle risque de ne pas être résolue.
>* La résolution des publicités différées n’a aucune incidence sur les publicités preroll.
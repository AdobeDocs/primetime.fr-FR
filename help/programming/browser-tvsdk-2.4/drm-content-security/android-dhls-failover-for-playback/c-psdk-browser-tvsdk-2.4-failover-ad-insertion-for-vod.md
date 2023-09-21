---
description: Le processus d’insertion de publicités par vidéo à la demande (VOD) comprend les phases de résolution, d’insertion de publicités et de lecture de publicités. Pour le suivi des publicités, le TVSDK du navigateur doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, il prend les mesures appropriées.
title: Insertion et basculement publicitaires pour VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Insertion et basculement publicitaires pour VOD{#advertising-insertion-and-failover-for-vod}

Le processus d’insertion de publicités par vidéo à la demande (VOD) comprend les phases de résolution, d’insertion de publicités et de lecture de publicités. Pour le suivi des publicités, le TVSDK du navigateur doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, il prend les mesures appropriées.

## Phase de résolution des publicités {#section_F562CD6D0EF04AA9A0A3C0176A4EC340}

Le navigateur TVSDK contacte un service de diffusion publicitaire, tel que Adobe Primetime Ad Decisioning, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Pendant la phase de résolution des publicités, le navigateur TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.

Le navigateur TVSDK prend en charge les types de fournisseurs d’annonces suivants :

* Fournisseur de publicités de métadonnées

  Les données de publicité sont codées dans des fichiers JSON en texte brut.
* Fournisseur d’annonces de prise de décision publicitaire Adobe Primetime

  Le TVSDK du navigateur envoie une demande, y compris un ensemble de paramètres de ciblage et un numéro d’identification des ressources, au serveur principal Adobe Primetime Ad Decisioning. Adobe Primetime Ad Decisioning répond avec un document SMIL (synchronized multimédia integration language) contenant les informations sur la publicité requises.

  L’une des situations de basculement suivantes peut se produire au cours de cette phase :

   * Les données ne peuvent pas être récupérées pour des raisons telles qu’un manque de connectivité ou une erreur côté serveur, telle qu’une ressource introuvable, etc.
   * Les données ont été récupérées, mais le format n’est pas valide.

     Cela peut se produire car, par exemple, l’analyse des données entrantes a échoué.

  Le navigateur TVSDK émet une notification d’avertissement à propos de l’erreur et continue le traitement.

## Phase d’insertion publicitaire {#section_88A0E4FA12394717A9D85689BD11D59F}

Le navigateur TVSDK insère dans la chronologie le contenu alternatif (publicités) correspondant au contenu principal.

Une fois la phase de résolution des publicités terminée, le TVSDK du navigateur dispose d’une liste classée de ressources publicitaires regroupées en coupures publicitaires. Chaque coupure publicitaire est positionnée sur la chronologie du contenu principal à l’aide d’une valeur de début exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété duration également exprimée en ms. Les publicités d’une coupure publicitaire sont enchaînées les unes après les autres. Par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut se produire au cours de cette phase avec des conflits qui peuvent se produire sur la chronologie lors de l’insertion de publicités. Pour des combinaisons spécifiques de valeurs d’heure de début/durée de coupure publicitaire, les segments de publicité peuvent se chevaucher. Le chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité dans la coupure publicitaire suivante. Dans ce cas, le TVSDK du navigateur ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant dans la liste jusqu’à ce que tous les coupures publicitaires soient insérés ou ignorés.

Le navigateur TVSDK émet une notification d’avertissement à propos de l’erreur et continue le traitement.

## Phase de lecture de la publicité {#section_7B0073BE9A744C74929263182C1243FC}

Le navigateur TVSDK télécharge les segments de publicité et les restitue sur l’écran de l’appareil.

À ce stade, le navigateur TVSDK a résolu les publicités, les a placées dans la chronologie et tente d’afficher le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire dans cette phase :

* Erreurs lors de la connexion au serveur hôte
* Erreurs lors du téléchargement du fichier manifeste
* Erreurs lors du téléchargement des segments multimédia

Pour les trois classes d’erreur, le navigateur TVSDK transmet les événements déclenchés à votre application, notamment :

* Événements de notification déclenchés en cas de basculement.
* Événements de notification lorsque le profil est modifié en raison de l’algorithme de basculement.
* Événements de notification déclenchés lorsque toutes les options de basculement ont été prises en compte et qu’aucune action supplémentaire ne peut être effectuée automatiquement.

  Votre application doit prendre les mesures appropriées.

Que des erreurs se soient produites ou non, le TVSDK du navigateur vous avertit lorsqu’une coupure publicitaire démarre et qu’elle se termine. Toutefois, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et la progression de la publicité signalée peuvent présenter des discontinuités.

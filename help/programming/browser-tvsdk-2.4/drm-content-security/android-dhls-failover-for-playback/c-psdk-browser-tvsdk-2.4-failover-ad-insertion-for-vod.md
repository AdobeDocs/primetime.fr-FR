---
description: Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion et de lecture des publicités. Pour le suivi des publicités, le navigateur TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, il prend les mesures appropriées.
seo-description: Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion et de lecture des publicités. Pour le suivi des publicités, le navigateur TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, il prend les mesures appropriées.
seo-title: Insertion et basculement publicitaires pour VOD
title: Insertion et basculement publicitaires pour VOD
uuid: 33f7aad5-fc4f-459d-8c29-01ba1353dfcc
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Insertion et basculement publicitaires pour VOD{#advertising-insertion-and-failover-for-vod}

Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion et de lecture des publicités. Pour le suivi des publicités, le navigateur TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, il prend les mesures appropriées.

## Phase de résolution des publicités {#section_F562CD6D0EF04AA9A0A3C0176A4EC340}

Le navigateur TVSDK contacte un service de  de publicité, tel qu’Adobe Primetime et la prise de décision publicitaire, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, le navigateur TVSDK effectue un appel HTTP au serveur ad-distant et analyse la réponse du serveur.

Le SDK du navigateur prend en charge les types de fournisseurs de publicités suivants :

* Fournisseur d’annonces de métadonnées

   Les données publicitaires sont codées dans des fichiers JSON en texte brut.
* Fournisseur publicitaire Adobe Primetime pour la prise de décision publicitaire

   Le navigateur TVSDK envoie une requête, y compris un ensemble de paramètres de ciblage et un numéro d’identification de fichier, au serveur principal Adobe Primetime et du serveur principal de prise de décision. La prise de décision publicitaire d’Adobe Primetime répond par un SMIL (langage d’intégration multimédia synchronisée) qui contient les informations publicitaires requises.

   L’une des situations de basculement suivantes peut se produire au cours de cette phase :

   * Les données ne peuvent pas être récupérées pour des raisons telles qu’un manque de connectivité ou une erreur côté serveur, telle qu’une ressource introuvable, etc.
   * Les données ont été récupérées, mais le format n&#39;est pas valide.

      Cela peut se produire en raison, par exemple, de l’échec de l’analyse des données entrantes.
   Le navigateur TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.

## Phase d&#39;insertion publicitaire {#section_88A0E4FA12394717A9D85689BD11D59F}

Le navigateur TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.

Une fois la phase de résolution des publicités terminée, le kit de développement logiciel du navigateur TVSDK comporte un ordonné de ressources publicitaires regroupées en pauses publicitaires. Chaque coupure publicitaire est positionnée sur le plan de montage chronologique du contenu principal à l’aide d’une valeur -temps exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété de durée qui est également exprimée en ms. Les publicités d’une coupure publicitaire sont liées les unes aux autres. Par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut survenir dans cette phase avec des conflits qui peuvent survenir sur le plan de montage chronologique lors de l’insertion d’une publicité. Pour des combinaisons spécifiques de valeurs de durée et d’heure de  des coupures publicitaires, les segments publicitaires peuvent se chevaucher. Le chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité au cours de la coupure publicitaire suivante. Dans ce cas, le navigateur TVSDK ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant sur le  jusqu’à ce que toutes les coupures publicitaires soient insérées ou ignorées.

Le navigateur TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.

## Phase de lecture publicitaire {#section_7B0073BE9A744C74929263182C1243FC}

Le navigateur TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.

A ce stade, le navigateur TVSDK a résolu les publicités, les a placées sur la chronologie et tente de rendre le contenu à l’écran.

Les principales classes d’erreurs suivantes peuvent se produire au cours de cette phase :

* Erreurs lors de la connexion au serveur hôte
* Erreurs lors du téléchargement du fichier manifeste
* Erreurs lors du téléchargement des segments de médias

Pour les trois classes d’erreur, le navigateur TVSDK a déclenché  à votre application, notamment :

* de notification déclenché lorsqu’un basculement survient.
* de notification lorsque le  est modifié en raison de l’algorithme de basculement.
* Le de notification  déclenché lorsque toutes les options de basculement ont été prises en compte et qu’aucune action supplémentaire ne peut être effectuée automatiquement.

   Votre application doit prendre les mesures appropriées.

Que des erreurs se produisent ou non, le navigateur TVSDK vous avertit lorsqu’un de coupure publicitaire se  et lorsqu’il se termine. Toutefois, si les segments n’ont pas pu être téléchargés, il se peut qu’il y ait des lacunes dans la chronologie. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et de la progression de la publicité rapportée peuvent présenter des discontinuités.

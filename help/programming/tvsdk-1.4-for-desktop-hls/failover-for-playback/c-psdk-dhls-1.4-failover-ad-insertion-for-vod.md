---
description: Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion publicitaire et de lecture publicitaire. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues se présentent, il prend les mesures appropriées.
seo-description: Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion publicitaire et de lecture publicitaire. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues se présentent, il prend les mesures appropriées.
seo-title: Insertion et basculement publicitaires pour VOD
title: Insertion et basculement publicitaires pour VOD
uuid: 98505f63-ac43-4ff5-9f7b-895b6135df47
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Insertion et basculement publicitaires pour VOD{#advertising-insertion-and-failover-for-vod}

Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion publicitaire et de lecture publicitaire. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues se présentent, il prend les mesures appropriées.

## Phase de résolution des publicités {#section_0D45C6094D724B55868B48F9A3557A8B}

TVSDK contacte un service de diffusion publicitaire, tel qu’Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.

TVSDK prend en charge les types de fournisseurs d’annonces suivants :

* Fournisseur d’annonces de métadonnées

   Les données publicitaires sont codées dans des fichiers JSON en texte brut.
* Fournisseur publicitaire de décision publicitaire Primetime

   TVSDK envoie une requête, y compris un ensemble de paramètres de ciblage et un numéro d’identification de ressource, au serveur principal Primetime et de prise de décision. La prise de décision publicitaire Primetime répond par un document SMIL (synchronized multimédia integration language) qui contient les informations publicitaires requises.

Une des situations de basculement suivantes peut se produire pendant cette phase :

* Les données ne peuvent pas être récupérées pour des raisons telles qu&#39;un manque de connectivité ou une erreur côté serveur, telle qu&#39;une ressource introuvable, etc.
* Les données ont été récupérées, mais le format n&#39;est pas valide.

   Cela peut se produire en raison, par exemple, de l’échec de l’analyse des données entrantes.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.

## Phase d&#39;insertion publicitaire {#section_1B18E8B5768B4873B3346294175B7340}

TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.

Une fois la phase de résolution de la publicité terminée, TVSDK dispose d’une liste ordonnée de ressources publicitaires regroupées en pauses publicitaires. Chaque coupure publicitaire est positionnée sur la chronologie du contenu principal à l’aide d’une valeur de début-temps exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété de durée qui est également exprimée en ms. Les publicités d’une coupure publicitaire sont chaînées les unes après les autres. Par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut survenir au cours de cette phase avec des conflits qui peuvent survenir sur le plan de montage chronologique lors de l&#39;insertion d&#39;une publicité. Pour des combinaisons spécifiques de valeurs de début/durée de coupure publicitaire, les segments publicitaires peuvent se chevaucher. Le chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité au cours de la coupure publicitaire suivante. Dans ce cas, ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant de la liste jusqu’à ce que toutes les coupures publicitaires soient insérées ou ignorées.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.

## Phase de lecture publicitaire {#section_64777BD2CDA84EACB0A4EA6D68367CF5}

TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.

À ce stade, TVSDK a résolu les publicités, les a placées sur la chronologie et tente de rendre le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire au cours de cette phase :

* Erreurs lors de la connexion au serveur hôte
* Erreurs lors du téléchargement du fichier manifeste
* Erreurs lors du téléchargement des segments de médias

Pour les trois classes d’erreur, TVSDK transmet les événements déclenchés à votre application, notamment :

* événements de notification déclenchés en cas de basculement.
* La notification s’événement lorsque le profil est modifié en raison de l’algorithme de basculement.
* événements de notification déclenchés lorsque toutes les options de basculement ont été prises en compte et qu&#39;aucune action supplémentaire ne peut être exécutée automatiquement.

   Votre application doit prendre les mesures appropriées.

Que des erreurs se produisent ou non, TVSDK appelle `AdBreakPlaybackEvent.AD_BREAK_COMPLETE` pour chaque `AdBreakPlaybackEvent.AD_BREAK_STARTED` et `AdPlaybackEvent.AD_COMPLETED` pour chaque `AdPLaybackEvent.AD_STARTED`variable. Cependant, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et de la progression de la publicité signalée peuvent présenter des discontinuités.

---
description: Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion publicitaire et de lecture publicitaire. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, TVSDK prend les mesures appropriées.
seo-description: Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion publicitaire et de lecture publicitaire. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, TVSDK prend les mesures appropriées.
seo-title: Insertion et basculement publicitaires pour VOD
title: Insertion et basculement publicitaires pour VOD
uuid: 74cc35e6-6479-4572-a3b3-05ff6344272a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Insertion et basculement publicitaires pour VOD {#advertising-insertion-and-failover-for-vod}

Le processus d’insertion publicitaire vidéo à la demande (VOD) comprend les phases de résolution, d’insertion publicitaire et de lecture publicitaire. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, TVSDK prend les mesures appropriées.

## Phase de résolution des publicités {#section_5DD3A7DA79E946298BFF829A60202E1C}

TVSDK contacte un service de diffusion publicitaire, tel qu’Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal correspondant au flux vidéo de la publicité. Au cours de la phase de résolution des publicités, TVSDK effectue un appel HTTP au serveur de diffusion publicitaire distant et analyse la réponse du serveur.

TVSDK prend en charge les types de fournisseurs d’annonces suivants :

* Fournisseur d’annonces de métadonnées

   Les données publicitaires sont codées dans des fichiers JSON en texte brut.
* Fournisseur publicitaire de décision publicitaire Primetime

   TVSDK envoie une requête, y compris un ensemble de paramètres de ciblage et un numéro d’identification de la ressource, au serveur principal Primetime et de décision. La prise de décision publicitaire Primetime répond à un document d’intégration multimédia synchronisée (SMIL) qui contient les informations publicitaires requises.
* Fournisseur de marques publicitaires personnalisées

   Gère la situation où les publicités sont brûlées dans le flux, du côté serveur. TVSDK n’effectue pas l’insertion réelle de la publicité, mais il doit effectuer le suivi des publicités insérées côté serveur. Ce fournisseur définit les marqueurs publicitaires utilisés par TVSDK pour effectuer le suivi des publicités.

Une des situations de basculement suivantes peut se produire pendant cette phase :

* Les données ne peuvent pas être récupérées en raison, par exemple, du manque de connectivité ou d&#39;une erreur côté serveur, telle qu&#39;une ressource introuvable, etc.
* Les données ont été récupérées, mais le format n&#39;est pas valide.

   Cela peut se produire en raison, par exemple, de l’échec de l’analyse des données entrantes.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.

## Phase d&#39;insertion publicitaire {#section_29F7F7756C8B40B99AD4C3DD16B72B5B}

TVSDK insère le contenu alternatif (publicités) dans la chronologie qui correspond au contenu principal.

Une fois la phase de résolution de la publicité terminée, TVSDK dispose d’une liste ordonnée de ressources publicitaires regroupées en pauses publicitaires. Chaque coupure publicitaire est positionnée sur la chronologie du contenu principal en utilisant une valeur de début-temps exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété de durée qui est également exprimée en ms. Les publicités d’une coupure publicitaire sont chaînées et, par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composées individuelles.

Le basculement peut survenir au cours de cette phase avec des conflits qui peuvent survenir sur le plan de montage chronologique lors de l&#39;insertion d&#39;une publicité. Pour des combinaisons spécifiques de valeurs de début/durée de coupure publicitaire, les segments publicitaires peuvent se chevaucher. Ce chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité au cours de la coupure publicitaire suivante. Dans ce cas, TVSDK ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant de la liste jusqu’à ce que toutes les coupures publicitaires soient insérées ou ignorées.

TVSDK émet une notification d’avertissement concernant l’erreur et poursuit le traitement.

## Phase de lecture publicitaire {#section_DA816F88AF8A4A5A8FD0DE2D54A86031}

TVSDK télécharge les segments d’annonce et les rend sur l’écran du périphérique.

TVSDK a maintenant résolu les publicités, positionné les publicités sur la chronologie et tente de rendre le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire au cours des phases suivantes :

* Lors de la connexion au serveur hôte.
* Lors du téléchargement du fichier manifeste.
* Lors du téléchargement des segments de médias.

TVSDK transmet les événements déclenchés à votre application, y compris les événements de notification déclenchés lorsque :

* Un basculement a lieu.
* Le profil est modifié en raison de l’algorithme de basculement.
* Toutes les options de basculement ont été prises en compte et aucune action supplémentaire ne peut être effectuée automatiquement.

   Votre application doit prendre les mesures appropriées.

Que des erreurs se produisent ou non, TVSDK appelle `onAdBreakComplete` pour chaque `onAdBreakStart` et `onAdComplete` pour chaque `onAdStart`variable. Cependant, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et de la progression de la publicité signalée peuvent présenter des discontinuités.
---
description: Le processus d’insertion de publicités par vidéo à la demande (VOD) comprend les phases de résolution, d’insertion de publicités et de lecture de publicités. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, TVSDK prend les mesures appropriées.
title: Insertion et basculement publicitaires pour VOD
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 0%

---

# Insertion et basculement publicitaires pour VOD {#advertising-insertion-and-failover-for-vod}

Le processus d’insertion de publicités par vidéo à la demande (VOD) comprend les phases de résolution, d’insertion de publicités et de lecture de publicités. Pour le suivi des publicités, TVSDK doit informer un serveur de suivi distant de la progression de la lecture de chaque publicité. Lorsque des situations inattendues surviennent, TVSDK prend les mesures appropriées.

## Phase de résolution des publicités {#section_5DD3A7DA79E946298BFF829A60202E1C}

TVSDK contacte un service de diffusion publicitaire, tel que la prise de décision publicitaire Adobe Primetime, et tente d’obtenir le fichier de liste de lecture principal qui correspond au flux vidéo de la publicité. Pendant la phase de résolution de la publicité, TVSDK effectue un appel HTTP au serveur de diffusion de publicité distante et analyse la réponse du serveur.

TVSDK prend en charge les types de fournisseurs d’annonces suivants :

* Fournisseur de publicités de métadonnées

  Les données de publicité sont codées dans des fichiers JSON en texte brut.
* Fournisseur d’annonces de prise de décision publicitaire Primetime

  TVSDK envoie une demande, y compris un ensemble de paramètres de ciblage et un numéro d’identification de ressource, au serveur principal Primetime ad Decisioning. La prise de décision sur les publicités Primetime répond avec un document SMIL (Synchronized Media Integration Language) contenant les informations sur les publicités requises.
* Fournisseur de marketing publicitaire personnalisé

  Gère la situation où les publicités sont brûlées dans le flux, du côté serveur. TVSDK n’effectue pas l’insertion de publicités proprement dite, mais il doit effectuer le suivi des publicités insérées côté serveur. Ce fournisseur définit les marqueurs publicitaires utilisés par TVSDK pour effectuer le suivi des publicités.

L’une des situations de basculement suivantes peut se produire au cours de cette phase :

* Les données ne peuvent pas être récupérées en raison, par exemple, de l’absence de connectivité ou d’une erreur côté serveur, telle qu’une ressource, etc.
* Les données ont été récupérées, mais le format n’est pas valide.

  Cela peut se produire car, par exemple, l’analyse des données entrantes a échoué.

TVSDK émet une notification d’avertissement à propos de l’erreur et continue le traitement.

## Phase d’insertion publicitaire {#section_29F7F7756C8B40B99AD4C3DD16B72B5B}

TVSDK insère dans la chronologie le contenu alternatif (publicités) correspondant au contenu principal.

Une fois la phase de résolution des publicités terminée, TVSDK dispose d’une liste classée de ressources publicitaires qui sont regroupées en coupures publicitaires. Chaque coupure publicitaire est positionnée sur la chronologie du contenu principal à l’aide d’une valeur de début exprimée en millisecondes (ms). Chaque publicité d’une coupure publicitaire possède une propriété duration également exprimée en ms. Les publicités d’une coupure publicitaire sont chaînées et, par conséquent, la durée d’une coupure publicitaire est égale à la somme des durées des publicités composites individuelles.

Le basculement peut se produire au cours de cette phase avec des conflits qui peuvent se produire sur la chronologie lors de l’insertion de publicités. Pour des combinaisons spécifiques de valeurs d’heure de début/durée de coupure publicitaire, les segments de publicité peuvent se chevaucher. Ce chevauchement se produit lorsque la dernière partie d’une coupure publicitaire chevauche le début de la première publicité dans la coupure publicitaire suivante. Dans ce cas, TVSDK ignore la coupure publicitaire ultérieure et poursuit le processus d’insertion publicitaire avec l’élément suivant dans la liste jusqu’à ce que tous les coupures publicitaires soient insérés ou ignorés.

TVSDK émet une notification d’avertissement à propos de l’erreur et continue le traitement.

## Phase de lecture de la publicité {#section_DA816F88AF8A4A5A8FD0DE2D54A86031}

TVSDK télécharge les segments d’annonce et les affiche sur l’écran de l’appareil.

Désormais, TVSDK a résolu les publicités, les a positionnées dans la chronologie et tente d’afficher le contenu à l’écran.

Les principales classes d&#39;erreurs suivantes peuvent se produire lors des phases suivantes :

* Lors de la connexion au serveur hôte.
* Lors du téléchargement du fichier manifeste.
* Lors du téléchargement des segments multimédia.

TVSDK transfère les événements déclenchés à votre application, y compris les événements de notification déclenchés lorsque :

* Un basculement se produit.
* Le profil est modifié en raison de l’algorithme de basculement.
* Toutes les options de basculement ont été prises en compte et aucune action supplémentaire ne peut être effectuée automatiquement.

  Votre application doit prendre les mesures appropriées.

Que des erreurs se produisent ou non, les appels TVSDK `onAdBreakComplete` pour chaque `onAdBreakStart` et `onAdComplete` pour chaque `onAdStart`. Toutefois, si les segments n’ont pas pu être téléchargés, la chronologie peut présenter des lacunes. Lorsque les espaces sont suffisamment grands, les valeurs de la position du curseur de lecture et la progression de la publicité signalée peuvent présenter des discontinuités.

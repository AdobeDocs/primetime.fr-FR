---
title: Gestionnaires de fonctionnalités
description: Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du TVSDK à la recherche de code pour une fonctionnalité qui peut être éparpillée dans plusieurs emplacements.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Gestionnaires de fonctionnalités {#feature-managers}

Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du TVSDK à la recherche de code pour une fonctionnalité qui peut être éparpillée dans plusieurs emplacements. Les gestionnaires de fonctionnalités condensent le code en une classe par fonctionnalité. Les gestionnaires de fonctionnalités attendent les déclencheurs des événements TVSDK, puis informent la classe qui utilise le gestionnaire de fonctionnalités pour gérer le résultat. Le gestionnaire de fonctionnalités fournit les informations requises à la classe.

Les gestionnaires de fonctionnalités effectuent les tâches suivantes :

* **Fonctionnalités de Triggers TVSDK.**
Il s’agit d’appels de fonction pour déclencher une fonctionnalité TVSDK. Par exemple : `PlaybackManager.play()` est appelée lorsque l’application du lecteur doit démarrer la lecture vidéo.

* **Écoute les événements TVSDK.**
Le gestionnaire de fonctionnalités doit écouter les événements TVSDK pour obtenir des informations à partir de TVSDK. Par exemple : `AdsManager` écoute les événements TVSDK Ads pour être averti au démarrage de la coupure publicitaire.

* **Envoie les événements au gestionnaire.**
Une fois que les gestionnaires de fonctionnalités ont reçu et traité les événements de TVSDK, ils demandent au côté client de gérer l’événement. Par exemple, après `AdsManager` reçoit un événement de début de coupure publicitaire, il indique au fragment de lecteur de refléter cette modification dans l’interface utilisateur (désactiver la barre de défilement, afficher la superposition publicitaire, etc.).

La mise en oeuvre de la référence Primetime comprend les gestionnaires de fonctionnalités suivants :

| Gestionnaire de fonctionnalités | Fichier par défaut | Fonctionnalité |  |
|---|---|---|---|
| Lecture vidéo | PlaybackManager | Lecture et contrôle HLS, lecture et contrôle DVR, contrôle de mémoire tampon et gestion de débit multi-bits. | Obligatoire |
| Protection du contenu DRM | DrmManager | Protection du contenu. | Obligatoire |
| Insertion de publicités | AdsManager | Insertion d’annonces, y compris la coupure publicitaire directe et la coupure publicitaire personnalisée de la prise de décision publicitaire Adobe Primetime. | Facultatif |
| Sous-titres codés | CCManager | Sous-titres codés et VTT. | Facultatif |
| Liaison audio tardive | AAManager | Liaison audio tardive. | Facultatif |
| QoS | QosManager | Statistiques QoS. | Facultatif |
| Droit | EntitlementManager | Intégration des droits d’authentification Primetime. | Facultatif |

L’implémentation de référence contient des classes par défaut de base, répertoriées ci-dessus, ainsi que les classes correspondantes avec le suffixe On. Les classes par défaut fournissent les comportements TVSDK par défaut, tandis que les classes comportant le suffixe On incluent tout le code requis pour déclencher la fonctionnalité TVSDK et pour écouter les événements TVSDK correspondant à cette fonctionnalité.

* Pour les fonctionnalités facultatives, le code par défaut fonctionne comme si la fonction était désactivée.
* Les classes avec le suffixe On fonctionnent comme si la fonction était activée.

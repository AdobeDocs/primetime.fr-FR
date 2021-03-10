---
title: Gestionnaires de fonctionnalités
description: Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du SDK TVSDK à la recherche de code pour une fonction qui pourrait être dispersée en plusieurs emplacements.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---


# Gestionnaires de fonctionnalités {#feature-managers}

Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du SDK TVSDK à la recherche de code pour une fonction qui pourrait être dispersée en plusieurs emplacements. Les gestionnaires de fonctionnalités condensent le code en une classe par fonction. Les gestionnaires de fonctionnalités attendent les déclencheurs des événements TVSDK, puis informent la classe qui utilise le gestionnaire de fonctionnalités pour gérer le résultat. Le gestionnaire de fonctionnalités fournit les informations requises à la classe.

Les gestionnaires de fonctionnalités effectuent les tâches suivantes :

* **Déclenche les fonctionnalités de TVSDK.**
Il s’agit d’appels de fonction pour déclencher une fonction TVSDK. Par exemple, 
`PlaybackManager.play()` est appelée lorsque l’application du lecteur doit début la lecture vidéo.

* **Écoute les événements TVSDK.**
Le gestionnaire de fonctionnalités doit écouter les événements TVSDK pour obtenir des informations auprès de TVSDK. Par exemple, 
`AdsManager` écoute les événements d’annonces TVSDK pour être avertis lorsque la publicité tombe en début.

* **Distribue des événements au gestionnaire.**
Une fois que les gestionnaires de fonctionnalités ont reçu et traité les événements de TVSDK, ils avertissent le client de gérer le événement. Par exemple, après 
`AdsManager` reçoit un événement de début de coupure publicitaire, il indique au fragment du lecteur de refléter cette modification dans l’interface utilisateur (désactive la barre de défilement, affiche l’incrustation publicitaire, etc.).

L’implémentation de référence Primetime comprend les gestionnaires de fonctionnalités suivants :

| Gestionnaire de fonctionnalités | Fichier par défaut | Fonction |  |
|---|---|---|---|
| Lecture vidéo | PlaybackManager | Lecture et contrôle HLS, lecture et contrôle DVR, contrôle de la mémoire tampon et gestion des débits multibits. | Obligatoire |
| Protection du contenu DRM | DrmManager | Protection du contenu. | Obligatoire |
| Insertion publicitaire | AdsManager | Insertion d’une publicité, y compris prise de décision dans Adobe Primetime sur les coupures publicitaires directes et les coupures publicitaires personnalisées. | Facultatif |
| Sous-titres | CCManager | Sous-titrage et sous-titres VTT. | Facultatif |
| Audio à liaison tardive | AAManager | Liaison audio tardive. | Facultatif |
| QoS | QosManager | Statistiques de la qualité de service. | Facultatif |
| Droit | EntitlementManager | Intégration des droits d’authentification Primetime. | Facultatif |

L’implémentation de référence contient des classes par défaut de base, répertoriées ci-dessus, et des classes correspondantes avec le suffixe On. Les classes par défaut fournissent les comportements par défaut de TVSDK tandis que les classes avec le suffixe On incluent tout le code nécessaire pour déclencher la fonction TVSDK et écouter les événements TVSDK pour cette fonction.

* Pour les fonctionnalités facultatives, le code par défaut fonctionne comme si la fonction était désactivée.
* Les classes avec le suffixe Activé fonctionnent comme si la fonction était activée.
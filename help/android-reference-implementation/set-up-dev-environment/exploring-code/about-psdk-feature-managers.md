---
seo-title: Entraîneur de fonctionnalités
title: Entraîneur de fonctionnalités
uuid: 3d78544e-4819-4122-bfd3-01522a067aa9
description: Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du SDK TVSDK à la recherche de code pour une fonctionnalité qui pourrait être dispersée à plusieurs endroits.
seo-description: Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du SDK TVSDK à la recherche de code pour une fonctionnalité qui pourrait être dispersée à plusieurs endroits.
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Entraîneur de fonctionnalités {#feature-managers}

Les gestionnaires de fonctionnalités vous permettent de contrôler des fonctionnalités individuelles sans parcourir l’ensemble du SDK TVSDK à la recherche de code pour une fonctionnalité qui pourrait être dispersée à plusieurs endroits. Les gestionnaires de fonctionnalités condensent le code en une seule classe par fonctionnalité. Les gestionnaires de fonctionnalités attendent les déclencheurs des  TVSDK, puis informent la classe qui utilise le gestionnaire de fonctionnalités pour gérer le résultat. Le gestionnaire de fonctionnalités fournit les informations requises à la classe.

Les gestionnaires de fonctionnalités effectuent les  suivantes :

* **Déclenche les fonctionnalités de TVSDK.**
Il s’agit d’appels de fonction pour déclencher une fonction TVSDK. Par exemple, `PlaybackManager.play()` est appelée lorsque l’application du lecteur doit la lecture vidéo.

* **Écoute le TVSDK.**
Le gestionnaire de fonctionnalités doit écouter le TVSDK pour obtenir des informations auprès de TVSDK. Par exemple, `AdsManager` écoute le d’annonces TVSDK  être averti lorsque la publicité interrompt le .

* **Distribue  au gestionnaire.**
Une fois que les gestionnaires de fonctionnalités ont reçu et traité le  du kit TVSDK, ils avertissent le côté client de gérer le . Par exemple, après `AdsManager` réception d’un de coupure publicitaire  , le fragment du lecteur est informé de ce changement dans l’interface utilisateur (désactivez la barre de défilement, affichez l’incrustation publicitaire, etc.).

La mise en oeuvre de référence Primetime comprend les gestionnaires de fonctionnalités suivants :

| Gestionnaire de fonctionnalités | Fichier par défaut | Fonctionnalité |  |
|---|---|---|---|
| Lecture vidéo | PlaybackManager | Lecture et contrôle HLS, lecture et contrôle DVR, contrôle de la mémoire tampon et gestion des débits multibits. | Obligatoire |
| Protection du contenu DRM | DrmManager | Protection du contenu. | Obligatoire |
| Insertion d’une publicité | AdsManager | Insertion d’une publicité, y compris la prise de décision publicitaire directe Adobe Primetime et la coupure publicitaire personnalisée. | Facultatif |
| Sous-titres | CCManager | Sous-titrage et sous-titres VTT. | Facultatif |
| Audio à liaison tardive | AAManager | Liaison audio tardive. | Facultatif |
| QoS | QosManager | Statistiques de la qualité de service. | Facultatif |
| Droit | EntitlementManager | Intégration des droits d’authentification Primetime. | Facultatif |

L’implémentation de référence contient des classes par défaut de base, répertoriées ci-dessus, et des classes correspondantes avec le suffixe On. Les classes par défaut fournissent les comportements par défaut de TVSDK, tandis que les classes avec le suffixe On incluent tout le code requis pour déclencher la fonctionnalité TVSDK et écouter les  de TVSDK pour cette fonctionnalité.

* Pour les fonctionnalités facultatives, le code par défaut fonctionne comme si la fonction était désactivée.
* Les classes avec le suffixe Activé fonctionnent comme si la fonction était activée.
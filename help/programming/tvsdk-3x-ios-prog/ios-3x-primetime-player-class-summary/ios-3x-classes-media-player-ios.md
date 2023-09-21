---
description: Vous pouvez utiliser l’API Objective-C du lecteur Primetime pour personnaliser le comportement du lecteur.
title: Classes du lecteur multimédia
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Classes du lecteur multimédia {#media-player-classes}

Vous pouvez utiliser l’API Objective-C du lecteur Primetime pour personnaliser le comportement du lecteur.

Ces classes décrivent votre lecteur multimédia et ses ressources.

| Classe | Description |
|---|---|
| PTABRControlParameters | Encapsule tous les paramètres de contrôle de débit adaptatif. Les paramètres pris en charge sont les suivants :<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | Mise en oeuvre par défaut de PTMediaPlayerClientFactoryin dans TVSDK. Il fournit les instances availablePTOpportunityResolver, PTContentResolver et PTAdPolicySelector . |
| PTMediaPlayer | Définit le composant racine de la structure du lecteur Primetime. Les applications créent une instance de cette classe pour lire un média. Ce composant envoie des notifications pour informer votre application du statut du lecteur à un moment donné. |
| PTMediaPlayerClientFactory | Protocole qui décrit les méthodes qu’une fabrique de clients de lecteurs multimédia personnalisés doit implémenter pour fournir les instances PTOportunityResolver , PTContentResolver et PTAdPolicySelector disponibles. |
| PTMediaPlayerItem | Représente un média audio-vidéo spécifique. |
| PTMediaPlayerView | Gère le composant d’affichage de la structure du lecteur Primetime. |
| PTMediaProfile | Représente le profil d’un seul flux dans la liste de lecture des variantes. |
| PTMediaSelectionOption | Représente une ressource multimédia audiovisuelle afin de prendre en compte différentes préférences linguistiques, exigences d’accessibilité ou configurations d’application personnalisées. Types d’option valides :<ul><li>Sous-titres (PTMediaSelectionOptionTypeSubtitle)</li><li>Autre audio (PTMediaSelectionOptionTypeAudio)</li><li>Sous-titres codés (PTMediaSelectionOptionTypeCC)</li><li>Non définie (PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolver, classe, protocole PTOpportunityResolver | Classe utilisée pour le traitement de signaux in-manifest qui seront utilisés comme emplacements pour le processus de prise de décision publicitaire Adobe Primetime. |
| PTOpportunityResolverDelegate | Protocole qui décrit les méthodes que le programme de résolution d’opportunités personnalisé ( PTOpportunityResolver ) doit utiliser pour communiquer au délégué le statut de la résolution de l’opportunité. |
| PTSDK | Décrit la version de TVSDK et ses fonctionnalités. |
| PTSDKConfig | Expose les paramètres globaux TVSDK et permet à une application de s’abonner à des balises HLS personnalisées. |
| PTTextStyleRule | Définit des constantes qui représentent les clés d’attribut de style texte qui forment le dictionnaire des règles. |

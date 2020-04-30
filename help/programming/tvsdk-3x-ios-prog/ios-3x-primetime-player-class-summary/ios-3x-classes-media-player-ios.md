---
description: Vous pouvez utiliser l’API Objective-C du lecteur Primetime pour personnaliser le comportement du lecteur.
seo-description: Vous pouvez utiliser l’API Objective-C du lecteur Primetime pour personnaliser le comportement du lecteur.
seo-title: Classes du lecteur multimédia
title: Classes du lecteur multimédia
uuid: 705c71b6-4e5e-46b5-a59d-13df977b04f2
translation-type: tm+mt
source-git-commit: b13f2d3f083a6ca333a4edba1c8d7261f7d448ad

---


# Classes du lecteur multimédia {#media-player-classes}

Vous pouvez utiliser l’API Objective-C du lecteur Primetime pour personnaliser le comportement du lecteur.

Ces classes décrivent votre lecteur multimédia et ses ressources.

| Classe | Description |
|---|---|
| PTABRControlParameters | Encapsule tous les paramètres de contrôle de débit binaire adaptatif. Les paramètres pris en charge sont les suivants :<ul><li>minBitRate</li><li>maxBitRate</li><li>initialBitRate</li></ul> |
| PTDefaultMediaPlayerClientFactory | Mise en oeuvre par défaut de PTMediaPlayerClientFactoryin dans TVSDK. Il fournit les instances disponiblesPTOpportunityResolver, PTContentResolver et PTAdPolicySelector. |
| PTMediaPlayer | Définit le composant racine de la structure du lecteur Primetime.Les applications créent une instance de cette classe pour lire un média. Ce composant envoie des notifications pour informer votre application de l’état du lecteur à tout moment. |
| PTMediaPlayerClientFactory | Protocole décrivant les méthodes qu’une fabrique de clients de lecteur de médias personnalisée doit implémenter pour fournir les instances PTOpportunityResolver, PTContentResolver et PTAdPolicySelector disponibles. |
| PTMediaPlayerItem | Représente un média audio-vidéo spécifique. |
| PTMediaPlayerView | Gère le composant vue de la structure du lecteur Primetime. |
| PTMediaProfile | Représente l’profil d’un seul flux dans la liste de lecture variante. |
| PTMediaSelectionOption | Représente une ressource multimédia audiovisuelle pour répondre à différentes préférences linguistiques, exigences d’accessibilité ou configurations d’application personnalisées. Types d&#39;option valides :<ul><li>Sous-titres (PTMediaSelectionOptionTypeSubtitle)</li><li>Autre son (PTMediaSelectionOptionTypeAudio)</li><li>Sous-titres (PTMediaSelectionOptionTypeCC)</li><li>Non défini (PTMediaSelectionOptionTypeUndefined)</li></ul> |
| PTOpportunityResolver, classe,protocole PTOpportunityResolver | Classe utilisée pour le traitement d’indices manifestes qui seront utilisés comme emplacements pour le processus de prise de décision publicitaire Adobe Primetime. |
| PTOpportunityResolverDelegate | Protocole décrivant les méthodes que le résolveur d&#39;opportunités personnalisé ( PTOpportunityResolver ) doit utiliser pour communiquer au délégué l&#39;état de la résolution de l&#39;opportunité. |
| PTSDK | Décrit la version de TVSDK et ses fonctionnalités. |
| PTSDKConfig | Expose les paramètres généraux de TVSDK et permet à une application de s’abonner à des balises HLS personnalisées. |
| RègleStyleTexte | Définit des constantes qui représentent les clés d&#39;attribut de style de texte qui forment le dictionnaire de règles. |

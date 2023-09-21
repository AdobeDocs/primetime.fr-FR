---
description: L’insertion de publicités résout les publicités pour la diffusion vidéo à la demande (VOD) , pour la diffusion en direct et pour la diffusion en continu linéaire avec suivi des publicités et lecture de publicité. TVSDK envoie les demandes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et place les publicités dans le contenu par phases.
title: Insérer des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Insérer des publicités{#insert-ads}

L’insertion de publicités résout les publicités pour la diffusion vidéo à la demande (VOD) , pour la diffusion en direct et pour la diffusion en continu linéaire avec suivi des publicités et lecture de publicité. TVSDK envoie les demandes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et place les publicités dans le contenu par phases.

Un *`ad break`* contient une ou plusieurs publicités lues en séquence. TVSDK insère des publicités dans le contenu principal en tant que membres d’une ou de plusieurs coupures publicitaires.

>[!TIP]
>
>Si la publicité comporte des erreurs, TVSDK l’ignore.

## Résoudre et insérer des publicités VOD {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDK prend en charge plusieurs cas d’utilisation pour la résolution et l’insertion de publicités VOD.

* Insertion de publicités preroll, où les publicités sont insérées au début du contenu.
* Insertion de publicités mid-roll, où au moins une publicité est insérée au milieu du contenu.
* Insertion de publicités post-roll, où au moins une publicité est ajoutée à la fin du contenu.

TVSDK résout les publicités, insère les publicités dans les emplacements définis par le serveur de publicités et calcule la chronologie virtuelle avant le début de la lecture. Une fois la lecture commencée, aucune modification, telle que les publicités insérées ou insérées qui sont supprimées, ne peut se produire.

## Résoudre et insérer une publicité directe et linéaire {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDK prend en charge plusieurs cas d’utilisation pour la résolution et l’insertion de publicités en direct et linéaire.

* Insertion de publicités preroll, où au moins une publicité est insérée au début du contenu.
* Insertion de publicités mid-roll, où au moins une publicité est insérée au milieu du contenu.

TVSDK résout les publicités et insère les publicités lorsqu’un point de repère est rencontré dans le flux en direct ou linéaire. Par défaut, TVSDK prend en charge les indicateurs publicitaires valides suivants lors de la résolution et du placement d’annonces :

* #EXT-X-CUEPOINT
* #EXT-X-AD
* #EXT-X-CUE
* #EXT-X-CUE-OUT

Ces marqueurs requièrent le champ de métadonnées `DURATION` en secondes et l’identifiant unique du repère. Par exemple :

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

Pour plus d’informations sur d’autres indices, voir [Abonnement à des balises personnalisées](../ad-insertion/c-psdk-ios-1.4-custom-tags-configure/t-psdk-ios-1.4-custom-tags-subscribe.md).

## Suivi de la publicité client {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDK effectue automatiquement le suivi des publicités pour la diffusion VOD et la diffusion en continu directe/linéaire.

Les notifications sont utilisées pour informer votre application de la progression d’une publicité, notamment des informations sur le moment où une publicité commence et le moment où elle se termine.

## Mise en oeuvre d’un retour de coupure publicitaire anticipée {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

Pour l’insertion de publicités en continu, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

Voici quelques exemples d’un retour de coupure publicitaire anticipée :

* Durée de la coupure publicitaire dans certains événements sportifs.

  Bien qu’une durée par défaut soit fournie, si le jeu reprend avant que la coupure ne se termine, la coupure publicitaire doit être quittée.
* Signal d’urgence lors d’une coupure publicitaire dans un flux en direct.

La possibilité de quitter une coupure publicitaire plus tôt est identifiée par le biais d’une balise personnalisée dans le manifeste, appelée &quot;scintillement&quot; ou &quot;balise de repère&quot;. TVSDK permet à l’application de s’abonner à ces balises de division afin de fournir une opportunité de division.

* Pour utiliser la variable `#EXT-X-CUE-IN` marquez comme une opportunité de saut d’offre et implémentez un retour de coupure publicitaire anticipée :

   1. Abonnez-vous à la balise .

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. Ajoutez le résolveur d’opportunités de repère.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* Pour partager la même balise pour scission et scission :

   1. Si l’application partage le même indice pour indiquer une sortie/une scission et une entrée/une sortie, étendez `PTDefaultAdOpportunityResolver` et implémentez la variable `preparePlacementOpportunity` .

      >[!TIP]
      >
      >Le code suivant suppose que l’application possède une mise en oeuvre pour la variable `isCueInOpportunity` .
      >
      >```
      >- (PTPlacementOpportunity *)preparePlacementOpportunity:(PTTimedMetadata *)timedMetadata 
      >{ 
      >       if ([self isCueInOpportunity:timedMetadata]) 
      >       { 
      >               return [PTPlacementOpportunity advertisementSpliceInOpportunityWithTimedMetadata:timedMetadata]; 
      >       } 
      >       else 
      >       { 
      >               return [super preparePlacementOpportunity:timedMetadata]; 
      >       } 
      >}
      >```
      >

   1. Enregistrez le résolveur d’opportunité étendu sur la `PTDefaultMediaPlayerClientFactory` instance.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Clear existing resolver and register the new opportunity resolver 
      [clientFactory clearOpportunityResolvers]; 
      [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
      ```

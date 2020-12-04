---
description: L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en continu en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place par étapes dans le contenu.
seo-description: L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en continu en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place par étapes dans le contenu.
seo-title: Insérer des annonces
title: Insérer des annonces
uuid: 6e31cae5-7363-454f-82dd-e03c1e34cd3f
translation-type: tm+mt
source-git-commit: 23a48208ac1d3625ae7d925ab6bfba8f2a980766
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---


# Insérer des publicités {#insert-ads}

L’insertion d’une publicité résout les publicités pour la vidéo à la demande (VOD), pour la diffusion en continu en direct et pour la diffusion linéaire avec le suivi des publicités et la lecture des publicités. TVSDK envoie les requêtes requises au serveur d’annonces, reçoit des informations sur les publicités pour le contenu spécifié et les place par étapes dans le contenu.

Un *`ad break`* contient une ou plusieurs publicités lues en séquence. TVSDK insère des publicités dans le contenu principal en tant que membres d’une ou de plusieurs coupures publicitaires.

>[!TIP]
>
>Si la publicité comporte des erreurs, TVSDK ignore la publicité.

## Résolution et insertion de publicités VOD {#section_157344F857C64F36B48AD441F6E7FABA}

TVSDK prend en charge plusieurs cas d’utilisation pour la résolution et l’insertion de publicités VOD.

* Insertion publicitaire preroll, où les publicités sont insérées au début du contenu.
* Insertion d’une publicité intermédiaire, où au moins une publicité est insérée au milieu du contenu.
* Insertion d’une publicité post-roll, où au moins une publicité est ajoutée à la fin du contenu.

TVSDK résout les publicités, les insère dans les emplacements définis par le serveur d’annonces et calcule la chronologie virtuelle avant les débuts de lecture. Après les débuts de lecture, aucune modification, telle que les publicités insérées ou insérées supprimées, ne peut se produire.

## Résoudre et insérer une publicité directe et linéaire {#section_A6A1BB262D084462A1D134083556B7CC}

TVSDK prend en charge plusieurs cas d’utilisation pour la résolution et l’insertion de publicités en direct et linéaire.

* Insertion d’une publicité preroll, où au moins une publicité est insérée au début du contenu.
* Insertion d’une publicité intermédiaire, où au moins une publicité est insérée au milieu du contenu.

TVSDK résout les publicités et les insère lorsqu’un point de repère est détecté dans le flux en direct ou linéaire. Par défaut, TVSDK prend en charge les indices suivants en tant que marqueurs publicitaires valides lors de la résolution et du placement de publicités :

* # EXT-X-CUEPOINT
* # EXT-X-AD
* # EXT-X-CUE
* # EXT-X-CUE-OUT

Ces marqueurs nécessitent en secondes `DURATION` du champ de métadonnées et l’identifiant unique du signal. Par exemple :

```
#EXT-X-CUE DURATION=27 ID=identiferForThisCue ... 
```

Pour plus d&#39;informations sur d&#39;autres indices, voir [S&#39;abonner à des balises personnalisées](../../tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-custom-tags-configure/ios-3x-custom-tags-subscribe.md).

## Suivre la publicité cliente {#section_12355C7A35F14C15A2A18AAC90FEC2F5}

TVSDK effectue automatiquement le suivi des publicités pour VOD et pour la diffusion en flux continu directe/linéaire.

Les notifications sont utilisées pour informer votre application de l&#39;avancement d&#39;une publicité, y compris des informations sur le moment où une publicité commence et se termine.

## Mettre en oeuvre un retour de coupure publicitaire anticipée {#section_EEB9FE62CA7E4790B58D3CA906F43DCF}

Pour l’insertion de publicités en flux continu en direct, vous devrez peut-être quitter une coupure publicitaire avant que toutes les publicités de la coupure ne soient lues jusqu’à la fin.

Voici quelques exemples de retours de coupures publicitaires précoces :

* Durée de la coupure publicitaire dans certains événements sportifs.

   Bien qu’une durée par défaut soit fournie, si le jeu reprend avant que la coupure ne se termine, la coupure publicitaire doit être quittée.
* Signal d’urgence pendant une coupure publicitaire dans un flux en direct.

La possibilité de quitter une coupure publicitaire prématurée est identifiée par une balise personnalisée dans le manifeste, appelée &quot;splice-in&quot; ou &quot;indices-in&quot;. TVSDK permet à l’application de s’abonner à ces balises d’éclatement afin de fournir une opportunité d’éclatement.

* Pour utiliser la balise `#EXT-X-CUE-IN` en tant qu’opportunité de division et implémenter un retour de coupure publicitaire anticipée :

   1. Abonnez-vous à la balise .

      ```
      [PTSDKConfig setSubscribedTags:[NSArray arrayWithObject:@"#EXT-X-CUE-IN"]];
      ```

   1. Ajoutez le résolveur d&#39;opportunités de démarrage.

      ```
      // self.player is the PTMediaPlayer instance created for content and ad playback 
      PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
      
      // Set cue in opportunity resolver 
      [clientFactory registerOpportunityResolver:[PTDefaultAdSpliceInOpportunityResolver adSpliceInOpportunityResolverWithTag:@"#EXT-X-CUE-IN"]];
      ```

* Pour partager la même balise pour la division et la division :

1. Si l&#39;application partage le même indice pour indiquer le signal de départ/de sortie et le signal d&#39;arrivée/de sortie, étendez `PTDefaultAdOpportunityResolver` et implémentez la méthode `preparePlacementOpportunity`.

   >[!TIP]
   >
   >Le code suivant suppose que l’application a une implémentation pour la méthode `isCueInOpportunity`.

   ```
   - (PTPlacementOpportunity *)preparePlacementOpportunity:(PTTimedMetadata *)timedMetadata 
   { 
         if ([self isCueInOpportunity:timedMetadata]) 
         { 
               return [PTPlacementOpportunity advertisementSpliceInOpportunityWithTimedMetadata:timedMetadata]; 
           } 
           else 
           { 
               return [super preparePlacementOpportunity:timedMetadata]; 
         } 
   }
   ```

1. Enregistrez le résolveur d&#39;opportunité étendu sur l&#39;instance `PTDefaultMediaPlayerClientFactory`.

```
   // self.player is the PTMediaPlayer instance created for content and ad playback 
       PTDefaultMediaPlayerClientFactory *clientFactory = self.player.mediaPlayerClientFactory; 
             
   // Clear existing resolver and register the new opportunity resolver 
   [clientFactory clearOpportunityResolvers]; 
   [clientFactory registerOpportunityResolver:[[PTDefaultExtendedAdOpportunityResolver new] autorelease]];
```

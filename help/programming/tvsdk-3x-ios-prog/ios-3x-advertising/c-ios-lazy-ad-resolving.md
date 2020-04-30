---
description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. La fonction de résolution du chargement des publicités différé peut réduire ce délai de démarrage. Les publicités peuvent désormais être résolues à un intervalle spécifié avant la position de la coupure publicitaire. Pour y parvenir, il faut utiliser une approche à deux joueurs.
seo-description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. La fonction de résolution du chargement des publicités différé peut réduire ce délai de démarrage. Les publicités peuvent désormais être résolues à un intervalle spécifié avant la position de la coupure publicitaire. Pour y parvenir, il faut utiliser une approche à deux joueurs.
seo-title: Résolution des publicités juste à temps
title: Résolution des publicités juste à temps
uuid: f7b20439-3604-4d69-bdfe-2e0ad26f495b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Résolution des publicités juste à temps {#just-in-time-ad-resolving}

La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend la lecture au début. La fonction de résolution du chargement des publicités différé peut réduire ce délai de démarrage. Les publicités peuvent désormais être résolues à un intervalle spécifié avant la position de la coupure publicitaire. Pour y parvenir, il faut utiliser une approche à deux joueurs.

**Processus de base de résolution et de chargement des publicités :**

1. TVSDK télécharge un manifeste (playlist) et *résout* toutes les publicités.
1. TVSDK *charge* toutes les publicités et stimule les segments publicitaires dans les manifestes.
1. TVSDK déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.

Le lecteur utilise les URL du manifeste pour obtenir le contenu de la publicité (éléments créatifs), s’assure que le contenu de la publicité est dans un format lisible par TVSDK et TVSDK place les publicités sur la chronologie. Ce processus de base de résolution et de chargement des publicités peut provoquer un délai inacceptable pour un utilisateur attendant de lire son contenu, en particulier si le manifeste contient plusieurs URL de publicité.

**Résolution des publicités reluisantes :**

1. TVSDK télécharge la liste de lecture.
1. TVSDK *résout et charge* toutes les publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture de contenu commence.
1. TVSDK *résout* chaque coupure publicitaire avant sa position en fonction de la valeur définie dans `PTAdMetadata::delayAdLoadingTolerance`.

Par exemple, par défaut, `delayAdLoadingTolerance` est défini sur 5 secondes. Si un AdBreak est défini pour être lu à 3h00, il sera résolu à 2h55. Vous pouvez augmenter cette valeur si vous pensez que la résolution de votre publicité prendra plus de 5 secondes.

>[!IMPORTANT]
>
>**Facteurs à prendre en compte avec la résolution de publicités diffuses :**
>* La résolution des publicités différées n&#39;est prise en charge que pour les flux VOD avec les modes SERVER_MAP et le mode de signalisation.
>* La résolution des publicités différées n’est pas activée par défaut. Vous devez définir `PTAdMetadata::delayAdLoading` = YES pour l’activer.
>* La résolution des publicités différées est incompatible avec la fonction Instant On. Pour plus d’informations sur Instant On, voir [Instant On](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md).
>* Le mode Image dans l’image n’est pas pris en charge avec la résolution des publicités diffuses. Veuillez désactiver tous les modes d&#39;image si vous activez l&#39;option Résolution des publicités diffuses.
>* La résolution des publicités différées n’a aucune incidence sur les publicités preroll.
>


**Activer la résolution des annonces parentes**

Vous pouvez activer ou désactiver la fonction Résolution des publicités en différé à l’aide du mécanisme de chargement des publicités en différé existant (la résolution des publicités en différé est désactivée par défaut).

Vous pouvez activer la résolution des publicités différées en définissant `PTAdMetadata::delayAdLoading`= YES lors de la configuration des métadonnées publicitaires.

**API relatives à la résolution des publicités parentes :**

```
Class:    PTAdMetadata 
Properties: 
  
/** 
 * Property to define whether ad break resolution must be delayed until after stream start or not. 
 * When this value is NO, ads are resolved before stream start and spliced into the content when possible allowing  
   for a seamless playback experience. 
 * When this value is YES, ads are displayed in a secondary video player instance and resolved lazily only when  
   needed. 
 * Default value is NO 
 */ 
@property (nonatomic, assign) BOOL delayAdLoading; 
  
/** 
 * Property to define the lookahead for ad break resolution.  Ad breaks will be resolved when they occur between  
   the playhead time and the specified tolerance. 
 * If set to zero, the ad will be resolved immediately before playing the ad.  This may cause a slight delay in the  
   playback of the ads. 
 * Default value is 5.0 or 5 seconds. 
 */ 
  
@property (nonatomic, assign) NSTimeInterval delayAdLoadingTolerance;
```

---
description: La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend que la lecture démarre. La fonction Résolution du chargement différé des publicités peut réduire ce délai de démarrage. Les publicités peuvent désormais être résolues à un intervalle spécifié avant la position de la coupure publicitaire. Pour ce faire, vous devez utiliser une approche double du lecteur.
title: Résoudre les publicités juste à temps
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Résoudre les publicités juste à temps {#just-in-time-ad-resolving}

La résolution et le chargement des publicités peuvent provoquer un délai inacceptable pour un utilisateur qui attend que la lecture démarre. La fonction Résolution du chargement différé des publicités peut réduire ce délai de démarrage. Les publicités peuvent désormais être résolues à un intervalle spécifié avant la position de la coupure publicitaire. Pour ce faire, vous devez utiliser une approche double du lecteur.

**Processus de base de résolution et de chargement des publicités :**

1. TVSDK télécharge un manifeste (liste de lecture) et *résout* toutes les publicités.
1. TVSDK *chargements* toutes les publicités et regroupe les segments de publicité dans les manifestes.
1. TVSDK déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.

Le lecteur utilise les URL du manifeste pour obtenir le contenu de la publicité (éléments créatifs), s’assure que le contenu de la publicité est dans un format que TVSDK peut lire et que TVSDK place les publicités dans la chronologie. Ce processus de base de résolution et de chargement des publicités peut entraîner un délai inacceptable pour un utilisateur qui attend de lire son contenu, en particulier si le manifeste contient plusieurs URL d’annonce.

**Résoudre la publicité différée :**

1. TVSDK télécharge la liste de lecture.
1. TVSDK *résout et charge* toutes les publicités preroll, déplace le lecteur dans l’état PRÉPARÉ et la lecture du contenu commence.
1. TVSDK *résout* chaque coupure publicitaire avant sa position en fonction de la valeur définie dans `PTAdMetadata::delayAdLoadingTolerance`.

Par exemple, par défaut `delayAdLoadingTolerance` est définie sur 5 secondes. Si un AdBreak est défini pour être lu à 3 h 00, il sera résolu à 2 h 00.:55:00 Vous pouvez augmenter cette valeur si vous pensez que la résolution de votre publicité prendra plus de 5 secondes.

>[!IMPORTANT]
>
>**Facteurs à prendre en compte avec la résolution de publicités différée :**
>* La résolution des publicités différées n’est prise en charge que pour les flux VOD avec les modes SERVER_MAP et le mode de signalisation.
>* La résolution des publicités différées n’est pas activée par défaut. Vous devez définir `PTAdMetadata::delayAdLoading` = OUI pour l’activer.
>* La résolution différée des publicités est incompatible avec la fonction Instant On . Pour plus d’informations sur Instant On, voir [Instant activé](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md).
>* Le mode &quot;Image dans l’Image&quot; n’est pas pris en charge avec la résolution des publicités différées. Désactivez les modes Image dans l’Image si vous activez l’option Résolution des publicités différées.
>* La résolution différée des publicités n’a aucune incidence sur les publicités preroll.
>
**Activation de la résolution des publicités différées**

Vous pouvez activer ou désactiver la fonction Résolution des publicités différées à l’aide du mécanisme de chargement de publicités différées existant (la résolution des publicités différées est désactivée par défaut).

Vous pouvez activer la résolution des publicités différées en définissant `PTAdMetadata::delayAdLoading`= OUI lors de la configuration des métadonnées de votre publicité.

**API relatives à la résolution de publicités différée :**

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

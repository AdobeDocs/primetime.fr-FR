---
description: Lorsque la lecture atteint une coupure publicitaire, franchit une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
seo-description: Lorsque la lecture atteint une coupure publicitaire, franchit une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
seo-title: Personnalisation de la lecture avec des publicités
title: Personnalisation de la lecture avec des publicités
uuid: b21a2b1b-5376-41cb-a772-a8945fd56f3c
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Personnalisation de la lecture avec des publicités {#customize-playback-with-ads}

Lorsque la lecture atteint une coupure publicitaire, franchit une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.

>[!TIP]
>
>Vous pouvez remplacer le comportement par défaut en utilisant la `PTAdPolicySelector` classe.

Le comportement par défaut varie selon que l’utilisateur franchit la coupure publicitaire pendant la lecture normale ou effectue une recherche dans une vidéo.

Vous pouvez personnaliser le comportement de lecture des publicités de différentes manières :

* Enregistrez la position où l’utilisateur a arrêté de regarder la vidéo et recommencez la lecture à la même position lors d’une session ultérieure.
* Si une coupure publicitaire est présentée à l’utilisateur, n’affichez aucune publicité supplémentaire pendant un certain nombre de minutes, même si l’utilisateur cherche une nouvelle position.
* Si la lecture du contenu échoue au bout de quelques minutes, redémarrez le flux ou passez à une autre source pour le même contenu.

   Lors de la session de lecture sur le basculement, pour permettre à l’utilisateur de sauter des publicités et de reprendre la position d’échec précédente, vous pouvez désactiver les publicités preroll et/ou mid-roll. TVSDK fournit des méthodes permettant d’ignorer les publicités preroll et mid-roll.

## Eléments API pour la lecture de publicités {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.
Les éléments d’API suivants sont utiles pour personnaliser la lecture :

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Elément API</b></th> 
   <th colname="col2" class="entry"><b>Contenu prenant en charge la publicité</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata </span> </td> 
   <td colname="col2"> Indiquez si une coupure publicitaire doit être marquée comme ayant été regardée par un lecteur et, dans l’affirmative, quand la marquer. Définissez et obtenez la stratégie de contrôle à l’aide de <span class="codeph"> la propriété adBreakAsWatched </span> . </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector </span> </td> 
   <td colname="col2"> Protocole qui permet la personnalisation du comportement de l’annonce TVSDK. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Classe qui implémente le comportement par défaut de TVSDK. Votre application peut remplacer cette classe pour personnaliser les comportements par défaut sans mettre en oeuvre l’interface complète. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime </span>. <p>Il s’agit de l’heure locale de la lecture, à l’exclusion des coupures publicitaires importées. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> searchToLocalTime </span> . <p>Ici, la recherche se produit par rapport à une heure locale dans le flux. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTime </span>. <p>La position virtuelle sur le plan de montage chronologique est convertie en position locale. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched, </span> propriété. Indique si le lecteur a regardé la publicité. </td> 
  </tr> 
 </tbody> 
</table>

## Configuration de la lecture personnalisée {#section_8209BAACC7814C9399988DC7DE9CF4CA}

Avant de pouvoir personnaliser ou remplacer les comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec TVSDK.

Pour personnaliser les comportements publicitaires, effectuez l’une des opérations suivantes :

* Respectez le `PTAdPolicySelector` protocole et mettez en oeuvre toutes les méthodes de sélection de stratégie requises.

   Cette option est recommandée si vous devez remplacer **tous les** comportements publicitaires par défaut.

* Remplacez la `PTDefaultAdPolicySelector` classe et fournissez des implémentations uniquement pour les comportements nécessitant une personnalisation.

   Cette option est recommandée si vous ne devez remplacer que **certains** comportements par défaut.

Pour les deux options, complétez le  suivant :

1. Enregistrez l’instance de stratégie à utiliser par TVSDK via la fabrique de clients.

   >[!NOTE]
   >
   >Les stratégies publicitaires personnalisées enregistrées au début de la lecture sont effacées lorsque l’ `PTMediaPlayer` instance est délocalisée. Votre application doit enregistrer une instance de sélecteur de stratégies chaque fois qu’une nouvelle session de lecture est créée.

   Par exemple :

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Mettez en oeuvre vos personnalisations.

## Ignorer les coupures publicitaires pendant une période donnée {#section_99809BE4D9BB4DEEBBF596C746CA428A}

Par défaut, TVSDK force la lecture d’une coupure publicitaire lorsque l’utilisateur effectue une recherche sur une coupure publicitaire. Vous pouvez personnaliser le comportement pour ignorer une coupure publicitaire si le temps écoulé depuis la fin d’une coupure précédente se situe dans un certain nombre de minutes.

>[!IMPORTANT]
>
>En cas de recherche interne pour ignorer une publicité, il se peut qu’il y ait une légère pause dans la lecture.

L’exemple suivant d’un sélecteur de stratégie d’annonce personnalisée ignore les publicités au cours des cinq prochaines minutes (heure de l’horloge murale) après qu’un utilisateur ait vu une coupure publicitaire.

1. Enregistrez l’instance de stratégie à utiliser par TVSDK via la fabrique de clients.

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Mettez en oeuvre votre personnalisation.

**PTS5MinuteSkipBreakPolicySelector.h**

```
#import "PTMediaPlayerNotifications.h" 
#import "PTMediaPlayer.h" 
#import "PTDefaultAdPolicySelector.h" 
 
//  extend the default policy  
selector@interface PTS5MinuteSkipBreakPolicySelector : PTDefaultAdPolicySelector 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player; 
  
@end
```

**PTS5MinuteSkipBreakPolicySelector.m**

```
#import "PTS5MinuteSkipBreakPolicySelector.h" 
  
double MIN_BREAK_INTERVAL  = 60 * 5; // 5 minutes 
  
@implementation PTS5MinuteSkipBreakPolicySelector 
{ 
    PTMediaPlayer *_player; 
    NSTimeInterval _lastAdBreakPlayedTime; 
} 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player 
{ 
    if (self = [super init]) 
    { 
        _lastAdBreakPlayedTime = 0; 
        _player = [player retain]; 
        [self addobservers]; 
    } 
    
    return self; 
} 
  
- (NSArray *)selectAdBreaksToPlay:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectAdBreaksToPlay (%f): %f", self,  
        CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectAdBreaksToPlay:info]; 
    } 
    
    return nil; 
} 
  
- (PTAdBreakPolicyType)selectPolicyForAdBreak:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectPolicyForAdBreak (%f): %f  %f", self,  
            CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime,  
            [[NSDate date] timeIntervalSince1970]); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectPolicyForAdBreak:info]; 
    } 
    
    return PTAdBreakPolicyTypeSkip; 
} 
  
- (BOOL)shouldPlayAdBreaks 
{ 
    NSTimeInterval currentTime = [[NSDate date] timeIntervalSince1970]; 
    if (_lastAdBreakPlayedTime <= 0) 
    { 
        return YES; 
    } 
    
    if (_lastAdBreakPlayedTime > 0 && (currentTime - _lastAdBreakPlayedTime) > MIN_BREAK_INTERVAL) 
    { 
        return YES; 
    } 
    
    // don't play any ad break if 5 minutes hasn't elapsed 
    return NO; 
} 
  
- (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification 
{ 
    NSLog(@"%@ - AdBreak Start", self); 
} 
  
- (void) onMediaPlayerAdBreakCompleted:(NSNotification *) notification 
{ 
    _lastAdBreakPlayedTime = [[NSDate date] timeIntervalSince1970]; 
    NSLog(@"%@ - AdBreak Complete at: %f", self, _lastAdBreakPlayedTime); 
} 
  
- (void)addobservers 
{ 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
                name:PTMediaPlayerAdBreakStartedNotification object:_player]; 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
                name:PTMediaPlayerAdBreakCompletedNotification object:_player]; 
} 
  
- (void)removeObservers 
{ 
    [[NSNotificationCenter defaultCenter] removeObserver:self]; 
} 
  
- (void)dealloc 
{ 
    [self removeObservers]; 
    [_player release]; 
    [super dealloc]; 
} 
  
@end
```

## Enregistrer la position de la vidéo et reprendre ultérieurement {#section_FAE252E38CED48D4BDD38BAA4A6A20A4}

Vous pouvez enregistrer la position de lecture actuelle dans une vidéo et reprendre la lecture à la même position dans une session ultérieure.

Les publicités insérées dynamiquement diffèrent d’une session utilisateur à l’autre. Par conséquent, l’enregistrement de la position **avec** les publicités épissées fait référence à une position différente dans une session ultérieure. TVSDK fournit des méthodes pour récupérer la position de lecture tout en ignorant les publicités épissées.

1. Lorsque l’utilisateur ferme une vidéo, votre application récupère et enregistre la position dans la vidéo.

   >[!TIP]
   >
   >Les durées des publicités ne sont pas incluses.

   Les coupures publicitaires peuvent varier dans chaque session en raison des modèles publicitaires, du plafonnement des fréquences, etc. L’heure actuelle de la vidéo dans une session peut être différente dans une session ultérieure. Lors de l’enregistrement d’une position dans la vidéo, l’application récupère l’heure locale. Utilisez la `localTime` propriété pour lire cette position que vous pouvez enregistrer sur le périphérique ou dans une base de données sur le serveur.

   Par exemple, si l’utilisateur se trouve à la 20e minute de la vidéo et que cette position comprend cinq minutes de publicités, `currentTime` il y aura 1 200 secondes, alors `localTime` qu’à cette position il y aura 900 secondes.

   >[!IMPORTANT]
   >
   >L’heure locale et l’heure actuelle sont identiques pour les flux en direct/linéaires. Dans ce cas, `convertToLocalTime` n&#39;a aucun effet. Pour VOD, l’heure locale reste inchangée pendant la lecture des publicités.

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification { 
       CMTimeRange seekableRange = self.player.seekableRange; 
   
       if (CMTIMERANGE_IS_VALID(seekableRange)) { 
           double seekableRangeStart = CMTimeGetSeconds(seekableRange.start); 
           double seekableRangeDuration = CMTimeGetSeconds(seekableRange.duration); 
           double currentTime = CMTimeGetSeconds(self.player.currentTime); // includes ads 
           double localTime = CMTimeGetSeconds(self.player.localTime); // no ads 
       } 
   }
   ```

1. Pour reprendre la vidéo à la même position que celle enregistrée lors de la session précédente, utilisez `seekToLocalTime`.

   >[!TIP]
   >
   >Cette méthode est appelée uniquement avec des valeurs d’heure locale. Si la méthode est appelée avec les résultats de l’heure actuelle, un comportement incorrect se produit.

   Pour atteindre l’heure actuelle, utilisez `seekToTime`.

1. Lorsque votre application reçoit le  de modification de l’ `PTMediaPlayerStatusReady` état, recherchez l’heure locale enregistrée.

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. Fournissez les coupures publicitaires comme spécifié dans l’interface de la stratégie publicitaire.
1. Implémentez un sélecteur de stratégie d’annonce personnalisée en étendant le sélecteur de stratégie d’annonce par défaut.
1. Fournissez les coupures publicitaires qui doivent être présentées à l’utilisateur en implémentant `selectAdBreaksToPlay`

   >[!NOTE]
   >
   >Cette méthode comprend une coupure publicitaire preroll et des coupures publicitaires mid-roll avant la position horaire locale. Votre application peut décider de lire une coupure publicitaire preroll et de reprendre à l’heure locale spécifiée, de lire une coupure publicitaire mid-roll et de reprendre à l’heure locale spécifiée, ou de ne pas lire de coupures publicitaires.
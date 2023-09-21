---
description: Lorsque la lecture atteint une coupure publicitaire, transmet une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.
title: Personnalisation de la lecture avec des publicités
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# Personnalisation de la lecture avec des publicités{#customize-playback-with-ads}

Lorsque la lecture atteint une coupure publicitaire, transmet une coupure publicitaire ou se termine par une coupure publicitaire, TVSDK définit un comportement par défaut pour le positionnement du curseur de lecture actuel.

>[!TIP]
>
>Vous pouvez remplacer le comportement par défaut en utilisant la variable `PTAdPolicySelector` classe .

Le comportement par défaut varie, selon que l’utilisateur passe la coupure publicitaire lors de la lecture normale ou effectue une recherche dans une vidéo.

Vous pouvez personnaliser le comportement de lecture des publicités comme suit :

* Enregistrez la position où l’utilisateur a cessé de regarder la vidéo et a repris la lecture à la même position lors d’une session ultérieure.
* Si une coupure publicitaire est présentée à l’utilisateur, n’affiche aucune publicité supplémentaire pendant un certain nombre de minutes, même si l’utilisateur recherche une nouvelle position.
* Si la lecture du contenu échoue au bout de quelques minutes, redémarrez le flux ou passez à une autre source pour le même contenu.

  Lors de la session de lecture sur le basculement, pour permettre à l’utilisateur d’ignorer les publicités et de reprendre la position d’échec précédente, vous pouvez désactiver les publicités preroll et/ou mid-roll. TVSDK fournit des méthodes pour activer le saut des publicités preroll et mid-roll.

## Éléments d’API pour la lecture de publicité {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDK fournit des classes et des méthodes que vous pouvez utiliser pour personnaliser le comportement de lecture du contenu qui contient de la publicité.
Les éléments d’API suivants sont utiles pour personnaliser la lecture :

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Élément API </th> 
   <th colname="col2" class="entry"> Contenu prenant en charge la publicité </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata </span> </td> 
   <td colname="col2"> Permet de déterminer si une coupure publicitaire doit être marquée comme ayant été visionnée par une visionneuse et, dans l’affirmative, quand la marquer. Définissez et obtenez la stratégie de contrôle à l’aide de <span class="codeph"> adBreakAsWatched </span> . </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector </span> </td> 
   <td colname="col2"> Protocole qui permet la personnalisation du comportement publicitaire de TVSDK. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector </span> </td> 
   <td colname="col2"> Classe qui met en oeuvre le comportement par défaut de TVSDK. Votre application peut remplacer cette classe pour personnaliser les comportements par défaut sans mettre en oeuvre l’interface complète. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime </span>. <p>Il s’agit de l’heure locale de la lecture, à l’exception des coupures publicitaires placées. </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> searchToLocalTime </span> . <p>Ici, la recherche se produit par rapport à une heure locale dans le flux. </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTime </span>. <p>La position virtuelle sur la chronologie est convertie en position locale. </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched </span> . Indique si la visionneuse a visionné la publicité. </td> 
  </tr> 
 </tbody> 
</table>

## Configuration de la lecture personnalisée {#section_8209BAACC7814C9399988DC7DE9CF4CA}

Avant de pouvoir personnaliser ou remplacer les comportements publicitaires, enregistrez l’instance de stratégie publicitaire avec TVSDK.

Pour personnaliser les comportements d’annonce, effectuez l’une des opérations suivantes :

* Se conformer à la variable `PTAdPolicySelector` et mettre en oeuvre toutes les méthodes de sélection de stratégie requises.

  Cette option est recommandée si vous devez remplacer **all** les comportements publicitaires par défaut.

* Remplacer la variable `PTDefaultAdPolicySelector` et ne fournissent des implémentations que pour les comportements qui nécessitent une personnalisation.

  Cette option est recommandée si vous devez remplacer uniquement **some** des comportements par défaut.

Pour les deux options, effectuez les tâches suivantes :

1. Enregistrez l’instance de stratégie à utiliser par TVSDK via la fabrique cliente.

   >[!NOTE]
   >
   >Les stratégies de publicité personnalisées enregistrées au début de la lecture sont effacées lorsque la variable `PTMediaPlayer` instance est désaffectée. Votre application doit enregistrer une instance de sélecteur de stratégie chaque fois qu’une nouvelle session de lecture est créée.

   Par exemple :

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. Mettez en oeuvre vos personnalisations.

## Ignorer les coupures publicitaires pour une période {#section_99809BE4D9BB4DEEBBF596C746CA428A}

Par défaut, TVSDK force la lecture d’une coupure publicitaire lorsque l’utilisateur effectue une recherche sur une coupure publicitaire. Vous pouvez personnaliser le comportement pour ignorer une coupure publicitaire si le temps écoulé depuis la fin d’une coupure précédente se situe dans un certain nombre de minutes.

>[!IMPORTANT]
>
>En cas de recherche interne pour ignorer une publicité, il peut y avoir une légère pause dans la lecture.

L’exemple suivant d’un sélecteur de stratégie de publicité personnalisé ignore les publicités au cours des cinq prochaines minutes (heure du mur) après qu’un utilisateur a visionné une coupure publicitaire.

1. Enregistrez l’instance de stratégie à utiliser par TVSDK via la fabrique cliente.

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

Les publicités insérées dynamiquement diffèrent d’une session utilisateur à l’autre, ce qui permet d’enregistrer la position. **avec** les publicités épissées font référence à une position différente dans une session ultérieure. TVSDK fournit des méthodes pour récupérer la position de lecture tout en ignorant les publicités épissées.

1. Lorsque l’utilisateur quitte une vidéo, votre application récupère et enregistre la position dans la vidéo.

   >[!TIP]
   >
   >Les durées des publicités ne sont pas incluses.

   Les coupures publicitaires peuvent varier au cours de chaque session en raison des schémas publicitaires, de la limitation de fréquence, etc. L’heure actuelle de la vidéo dans une session peut être différente dans une session ultérieure. Lors de l’enregistrement d’une position dans la vidéo, l’application récupère l’heure locale . Utilisez la variable  `localTime` pour lire cette position que vous pouvez enregistrer sur le périphérique ou dans une base de données sur le serveur.

   Par exemple, si l’utilisateur se trouve à la 20e minute de la vidéo et que cette position inclut cinq minutes de publicités, `currentTime` sera de 1 200 secondes, tandis que `localTime` à cette position, il faudra 900 secondes.

   >[!IMPORTANT]
   >
   >L’heure locale et l’heure actuelle sont les mêmes pour les flux linéaire/en direct. Dans ce cas, `convertToLocalTime` n’a aucun effet. Pour VOD, l’heure locale reste inchangée pendant la lecture des publicités.

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

1. Pour reprendre la vidéo à la même position : pour reprendre la lecture de la vidéo à partir de la position enregistrée lors d’une session précédente, utilisez `seekToLocalTime`

   >[!TIP]
   >
   >Cette méthode est appelée uniquement avec les valeurs d’heure locale. Si la méthode est appelée avec les résultats de l’heure actuelle, un comportement incorrect se produit.

   Pour rechercher l’heure actuelle, utilisez `seekToTime`.

1. Lorsque votre demande reçoit la `PTMediaPlayerStatusReady` changement d’état, recherchez l’heure locale enregistrée.

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. Fournissez les coupures publicitaires comme indiqué dans l’interface de stratégie publicitaire.
1. Implémentez un sélecteur de stratégie de publicité personnalisé en étendant le sélecteur de stratégie de publicité par défaut.
1. Fournir les coupures publicitaires qui doivent être présentées à l’utilisateur en implémentant `selectAdBreaksToPlay`

   >[!NOTE]
   >
   >Cette méthode comprend une coupure publicitaire preroll et des coupures publicitaires mid-roll avant le poste horaire local. Votre application peut décider de lire une coupure publicitaire preroll et de reprendre à l’heure locale spécifiée, de lire une coupure publicitaire mid-roll et de reprendre à l’heure locale spécifiée ou de ne pas lire d’coupures publicitaires.
